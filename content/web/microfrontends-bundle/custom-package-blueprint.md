---
title: Custom package blueprint
layout: redirect
weight: 30
---

With micro frontends it is possible to add new functionality while the application is **running** (run-time), whereas the old approach only allowed new functionality to be added before the application was **built** (compile-time).

Blueprints are combinations of multiple UI functionalities that can be hosted by the platform (static files) and can be used to scaffold a new solution from scratch. On the other hand, a package is the composition of plugins and blueprints. As a blueprint can export plugins as well, they can be packed together into one package and deployed to the platform.

### Initialize the blueprint example {#initialize-the-blueprint-example}

1. Use the command shown below to start a multi-step process of creating a sample blueprint:

```js
c8ycli new
```

2. Select the plugin name, for example, "package-blueprint":

```js
? Enter the name of the project:  (my-application) package-blueprint
```

3. Select the version for which you want to create a sample application, for example, "1016.0.233", as micro frontends are supported with version higher then 10.16.0.0:

```console
? Which base version do you want to scaffold from?
  1015.0.372 (latest)
  1018.106.0 (next)
  1018.0.47
  1017.0.151
❯ 1016.0.233
  1014.0.359
  other
```

4. Select an application template as the basis for your plugin, in our case, "package-blueprint":

```console
? Which base project do you want to scaffold from?
  cockpit
  devicemanagement
  hybrid
> package-blueprint
  tutorial
  widget-plugin
  administration
```

After a few seconds, you should see the following message:

```console
Application created. Go into the folder "package-blueprint" and run npm install
```

5. Navigate to your application folder and execute `npm install`.

The application folder should look like the example shown below.
For this tutorial, the most important files are _package.json_ and _README.md_.

```console
app.module.spec.ts
jest.config.js
README.md
tsconfig.spec.json
app.module.ts
package.json
setup-jest.js
index.ts
polyfills.ts
tsconfig.json
```

You have now created your first package blueprint that uses Module Federation.

### Stepper setup (optional) {#stepper-setup-optional}

The `HOOK_STEPPER` can be additionally provided to allow application customization during the first load of an application. In this optional step we show a small single step example in which the user can select whether the navigator will be collapsed or not on startup.

1. Create a new _setup-step1.component.ts_ file with the following content:

```typescript
import { CdkStep } from "@angular/cdk/stepper";
import { Component } from "@angular/core";
import {
  AlertService,
  AppStateService,
  C8yStepper,
  SetupComponent,
} from "@c8y/ngx-components";

@Component({
  selector: "c8y-cockpit-setup-step1",
  templateUrl: "./setup-step1.component.html",
  host: { class: "d-contents" },
})
export class SetupStep1Component {
  config = {
    rootNodes: [],
    features: {
      alarms: true,
      dataExplorer: true,
      groups: true,
    },
    hideNavigator: false,
    userSpecificHomeDashboard: false,
  };
  pending = false;

  constructor(
    public stepper: C8yStepper,
    protected step: CdkStep,
    protected setup: SetupComponent,
    protected appState: AppStateService,
    protected alert: AlertService
  ) {}

  async next() {
    this.pending = true;
    try {
      const newConfig = { ...this.setup.data$.value, ...this.config };
      await this.appState.updateCurrentApplicationConfig(newConfig);
      this.setup.stepCompleted(this.stepper.selectedIndex);
      this.setup.data$.next(newConfig);
      this.stepper.next();
    } catch (ex) {
      this.alert.addServerFailure(ex);
    } finally {
      this.pending = false;
    }
  }

  back() {
    this.stepper.previous();
  }
}
```

2. Create a _setup-step1.component.html_ template:

```html
<form #stepForm="ngForm" name="form" class="d-contents">
  <div class="container-fluid flex-no-shrink fit-w">
    <div class="row separator-bottom">
      <div
        class="col-md-8 col-md-offset-2 col-lg-6 col-lg-offset-3 p-t-24 p-l-16 p-r-16"
      >
        <h3 translate class="text-medium l-h-base">Misc</h3>
        <p class="lead text-normal" translate>
          Miscellaneous settings for the current application.
        </p>
      </div>
    </div>
  </div>
  <div class="inner-scroll flex-grow">
    <div class="container-fluid fit-w">
      <div class="row">
        <div class="col-md-8 col-md-offset-2 col-lg-6 col-lg-offset-3">
          <c8y-misc-config [config]="config"></c8y-misc-config>
        </div>
      </div>
    </div>
  </div>
  <div class="card-footer separator d-flex j-c-center">
    <button
      class="btn btn-default"
      type="button"
      (click)="back()"
      *ngIf="index !== 0"
      translate
    >
      Previous
    </button>
    <button class="btn btn-primary" type="submit" (click)="next()" translate>
      Save and continue
    </button>
  </div>
</form>
```

3. Finally we extend the _app.module.ts_ file to include the new stepper components:

```typescript
import { NgModule } from "@angular/core";
import { BrowserAnimationsModule } from "@angular/platform-browser/animations";
import { AssetsNavigatorModule } from "@c8y/ngx-components/assets-navigator";
import { RouterModule as ngRouterModule } from "@angular/router";
import {
  CoreModule,
  BootstrapComponent,
  RouterModule,
  SetupStep,
  HOOK_STEPPER,
  Steppers,
  gettext,
} from "@c8y/ngx-components";
import { SetupStep1Component } from "./setup-step1.component";
import { DatapointLibraryModule } from "@c8y/ngx-components/datapoint-library";
import { MiscConfigComponent } from "./misc-config.component";

@NgModule({
  declarations: [SetupStep1Component, MiscConfigComponent],
  imports: [
    BrowserAnimationsModule,
    RouterModule.forRoot(),
    ngRouterModule.forRoot([], { enableTracing: false, useHash: true }),
    CoreModule.forRoot(),
    DatapointLibraryModule.forRoot(),
    AssetsNavigatorModule,
  ],
  providers: [
    {
      provide: HOOK_STEPPER,
      useValue: [
        {
          stepperId: Steppers.SETUP,
          component: SetupStep1Component,
          label: gettext("Step 1"),
          setupId: "exampleId",
          priority: 0,
        },
      ] as SetupStep[],
      multi: true,
    },
  ],
  bootstrap: [BootstrapComponent],
})
export class AppModule {}
```

Now on the first application start, users will have to complete the single step wizard above.

### Differences in approach to creating custom applications {#differences-in-approach-to-creating-custom-applications}

There are a couple of differences between a simple widget and one that is built according to the micro frontend guidelines.

The biggest difference is the _package.json_ file, where fields such as `isPackage` and `package` and `exports` (not in the current blueprint app) are located.
The following list shows the fields and what they are responsible for:

- `isPackage`: Indicates if the application is a package. In case of a widget that is added using a micro frontend, set the value to `true`.
- `package`: The type of package (for example, `blueprint`, but the type of the package can also be a plugin).
- `exports`: Important field. Defines the Angular modules that will be made available by the widget-plugin for the shell application (see also the _README.md_ file).
  - `name`: The name of the exported module.
  - `module`: The name of the Angular module class.
  - `path`: The path to the TypeScript file with the module.
  - `description`: A brief description of what the module does.
- `contextPath`: The context path tells on which URL your blueprint can be loaded. As this is also used to generate a global variable, choose a valid JavaScript variable. For example your `contextPath` should not start with a number. To avoid conflicts it is good practice to add a prefix to your context path, for example, the acronym of your company: `acme-`.
- `versioningMatrix`: Optional field which indicates the supported package versions and the recommended frontend and backend platform versions. If the package is not compatible with any of the recommended platform versions a warning is shown. The matrix must have the following format and all versions must be [SemVer](https://semver.org/). For example: `versioningMatrix: [{"1.0.0": {"api": ">1016.0.0", "sdk": ">1016.0.0"}}, {"2.0.0": {"api": ">1017.0.0", "sdk":">1017.0.0"}}]`. In case of repository-connect, versions which exist in the platform but are not included in the versioning matrix are removed during sync.

{{< c8y-admon-info >}}
A blueprint can also include plugins, which can later be used to extend other applications.
{{< /c8y-admon-info >}}

### Deployment {#deployment}

Uploading the package is the same as for regular widgets.
Execute the following commands sequentially:

```js
npm run build
```

and

```js
npm run deploy
```

Follow the console prompt to deploy the application to your tenant.
