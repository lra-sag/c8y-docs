---
weight: 10
title: Übersicht
layout: redirect
---

Die folgenden Abschnitte beschreiben detailliert alle Funktionalitäten der Cockpit-Anwendung.

Zur besseren Orientierung folgt eine Übersicht über den Inhalt dieses Dokuments.

<table>
<thead>
<colgroup>
   <col style="width: 20%;">
   <col style="width: 80%;">
</colgroup>
<tr>
<th align="left">Abschnitt</th>
<th align="left">Inhalt</th>
</tr>
</thead>
<tbody>
<tr>
<td align="left"><a href="#managing-assets">Verwalten von Assets</a></td>
<td align="left">Organisieren Sie Assets in <a href="#hierarchies">Hierarchien</a> durch <a href="#creating-groups">Erstellen von Gruppen</a> und <a href="#assigning-devices">Zuweisen von Geräten</a>.</td>
</tr>
<tr>
<td align="left"><a href="#data-explorer">Visualisieren von Daten mit dem Daten-Explorer</a></td>
<td align="left">Untersuchen, vergleichen und visualisieren Sie interaktiv IoT-Daten. <br> Beschreibt, wie Sie auf den <a href="#data-explorer">Daten-Explorer</a> zugreifen, <a href="#add-data-points">Datenpunkte</a> hinzufügen, <a href="#customize-data-points">Datenpunktattribute anpassen</a>, die <a href="#change-visualization">Visualisierung ändern</a>, den <a href="#create-widget">Daten-Explorer als Widget speichern</a> und Daten <a href="#export-data">exportieren</a>.</td>
</tr>
<tr>
<td align="left"><a href="#dashboards">Verwenden von Dashboards</a></td>
<td align="left"><a href="#creating-dashboards">Erstellen Sie Ihre eigenen Dashboards</a> durch Hinzufügen und Arrangieren von <a href="#adding-widgets">Widgets</a>. <a href="#sharing-dashboards">Teilen Sie Dashboards</a> unter allen Geräten des gleichen Typs.</td>
</tr>
<tr>
<td align="left"><a href="#widgets">Widgets-Sammlung</a></td>
<td align="left">Verwenden Sie verschiedene <a href="#widgets">Widget-Typen</a> aus der in Cumulocity IoT enthaltenen Widgets-Sammlung und konfigurieren Sie diese nach Ihren individuellen Bedürfnissen.</td>
</tr>
<tr>
<td align="left"><a href="../../benutzerhandbuch/device-management-de/#alarm-monitoring">Verwenden von Alarmen</a></td>
<td align="left">Überwachen Sie Probleme Ihrer Geräte mit Hilfe von Schweregraden und Prozessen. Da die Verwendung von Alarmen in der Cockpit-Anwendung exakt so funktioniert wie in der Device Management-Anwendung finden Sie weitere Informationen in <a href="../../benutzerhandbuch/device-management-de/#alarm-monitoring">Verwenden von Alarmen</a> unter Device Management.</td>
</tr>
<tr>
<td align="left"><a href="#reports">Verwalten von Berichten</a></td>
<td align="left">Bearbeiten Sie <a href="#reports">Berichte</a> auf Basis von Dashboard-Layouts, erstellen Sie <a href="#export">Berichte zum Exportieren von Daten</a> in das CSV- oder Excel-Format und <a href="#schedule-export">terminieren Sie den Export</a>.</td>
</tr>
<tr>
<td align="left"><a href="#data-point-library">Datenpunktbibliothek</a></td>
<td align="left">Verwalten Sie Standardeinstellungen ("Profile") Ihrer Geräte und wenden Sie diese mit Hilfe der <a href="#data-point-library">Datenpunktbibliothek</a> automatisch an.</td>
</tr>
<tr>
<td align="left"><a href="#smart-rules">Verwenden von Smart Rules</a></td>
<td align="left"><a href="#create-rules">Erstellen und verwalten Sie Geschäftsregeln</a>, um eingehende Daten in Echtzeit zu verarbeiten und entsprechende Aktionen auszuführen.</td>
</tr>
<tr>
<td align="left"><a href="#smart-rules-collection">Smart Rules-Sammlung</a></td>
<td align="left">Verwenden Sie vordefinierte <a href="#smart-rules-collection">globale Smart Rules</a> um Regeln zu konfigurieren, etwa für Geofencing, Alarmeskalation oder Benachrichtigungen (SMS/E-Mail). Beschreibt detailliert jede Smart Rule und ihre konfigurierbaren Parameter.</td>
</tr>
</tbody>
</table>

Mehr über allgemeine Aspekte der Cumulocity IoT-Plattform und ihrer Anwendungen erfahren Sie unter [Erste Schritte](/users-guide/overview).

### <a name="home"></a>Startseite

Bei der Startseite der Cockpit-Anwendung handelt es sich um ein Dashboard, das Daten für den Mandanten anzeigt.

![Home dashboard](/images/benutzerhandbuch/cockpit/cockpit-home-screen.png)

Die Daten, die auf der Startseite angezeigt werden, werden von allen Benutzern des Mandanten gemeinsam genutzt. Standardmäßig zeigt die Startseite eine Begrüßung, die aktiven kritischen Alarme, neueste Alarme und eine Karte mit allen Geräten.

Die Startseite kann nach Ihren eigenen Bedürfnissen bearbeitet und gestaltet werden. Sie können die angezeigten Widgets ändern oder entfernen oder neue Widgets hinzufügen.

Details zum Bearbeiten von Dashboards finden Sie unter [Arbeiten mit Dashboards](#dashboards).

Um die Startseite wieder auf die ursprünglichen Inhalte zurückzusetzen, klicken Sie **Mehr...** rechts oben in der Menüleiste und klicken Sie dann **Dashboard wiederherstellen**.