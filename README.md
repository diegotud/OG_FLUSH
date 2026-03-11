[English](#og_flush) | [Deutsch](#og_flush-de)

---
# **OG_FLUSH**

## Description
**OG_FLUSH** (**O**pen-access **G**IS-based **F**low **L**ayout for **U**rban **S**ewer **H**ydrodynamics) is a QGIS plugin. It's developed for automatically generating a sewer system based on open-source geodata inputs, ideally the open-access source OpenStreetMaps. The outputs are then used to generate a hydrodynamic sewer system model like the Storm Water Management Model (SWMM).

The conceptual details and methodology can be found at https://www.mdpi.com/2073-4441/15/1/46.

This Tool was developed under the scope of the KlimaKonform project. Further information can be found here at https://klimakonform.uw.tu-dresden.de.



<br>

## Inputs
The following inputs are necessary for this plugin.


| Parameter | Requirment | Type | Description | Source |
| --- | --- | --- | --- | --- |
| Study area | Required | ESRI Polygon Shapefile | Boundary defining the area of interest | User-defined |
| Outlet | Required | ESRI Point Shapefile | Single endpoint for the network (e.g., treatment plant or discharge location) | User-defined |
| Buildings | Required | ESRI Polygon Shapefile | Building footprints within the study area | Various (e.g. OSM, Google Open Buildings) |
| Streets | Required | ESRI LineString Shapefile | OSM-based road network guiding the sewer design alignment | OSM |
| Digital elevation model | Required | Raster | Elevation data representing terrain heights | Various (e.g. city portals) |
| Population density | Optional | ESRI Point Shapefile | Population distribution for combined sewer design | Various (e.g. OSM) |


<br>

## Preparation
The following points should be considered to prepare the input files.
1.	Please ensure that all the inputs are in a UTM coordinate system.
2.	Please ensure that the extent of Buildings, Streets, Elevation and Population Density data covers the whole Study Area. One way to achieve this is to get a buffer of the Study Area and extract the data using the buffered area.
3.	Please ensure that all the plugin dependencies are available in QGIS. For more information, see the **External Dependencies** section.


<br>

## External Dependencies
OG.FLUSH depends on three Python libraries for operation, namely NetworkX, NumPy and Pandas. While some of these libraries might already be included in a QGIS environment, they also might not. In the case of such unavailability, the user has to install these libraries to use the plugin. To install these, you can follow the steps given below.

If QGIS has been installed with the official OSGeo4W installer, the OSGeo4W Shell can be used to install the required libraries.  
1.  First, search for "OSGeo4W Shell" in your Windows Start Menu and click to open it.  
2.  At the command prompt, type (or just copy) the following command to check if pip is installed.  
    `python -m pip --version`  
3.  If the console shows pip as already installed, proceed to step 4. Otherwise, type the following command to install pip.  
    `python -m ensurepip --upgrade`  
4.  Once pip is installed, type the following command to install the required libraries.  
    `python -m pip install networkx numpy pandas`  
5.  The console will download and install the missing libraries and skip the ones already installed.  
6.  Once done, close the shell, restart QGIS and the plugin should work.  

QGIS' own Python Console can be used to install the libraries as well, if pip is already installed.  
1.  In QGIS, go to **Plugins** → **Python Console**. The console should appear, usually at the bottom of the QGIS window.  
2.  After the ">>>", type or copy the following lines one by one and press **Enter** after each line.  
    `import pip`  
    `pip install networkx numpy pandas`  
3.  Similar to the previous method, the console will download and install the necessary libraries.  
4.  Once done, restart QGIS and the plugin should also work.


<br>

## Instructions
1.	First, you have to install the plugin in QGIS.  
  a.	Go to **Plugins** → **All**.  
  b.	Search for **OG.FLUSH**.  
  c.    Click on **Install Plugin**.
2.	Once the plugin is installed, click on the icon* on the toolbar.  
    **It currently looks like a blue network. One day, we hope to hire a professional designer.*  
3.	If you don't see the plugin in the interface or on the installed list, try toggling it on and off in the Plugin Manager or restarting QGIS.
4.	Select the shapefiles needed from the dropdown menu. If they are loaded in QGIS, they can appear in their corresponding fields, otherwise, you can browse for them with the **…** button.  
5.	Select the design parameters according to local regulations. There is more information for them in the pop-up messages if you hover your mouse above the fields.  
6.	If you want to design a combined system, click on the checkbox and input the necessary data.  
7.	If you want to add meshness, as in additional pipes in the network for many reasons (e.g. having more storage), put how much in percentage of the ones skipped during the main design.  
8.	Select an output folder for your files.  
9.	Click the “Run” button.  
10.	If QGIS freezes for a couple of minutes, don't worry. Just let it work. Meanwhile, the progress bar should keep you company.  


<br>

## Assumptions and Limitations
1.	All sewers are designed along the streets (technically, under).
2.	The rational method is used for sewer pipe dimensions.
3.	Lower-resolution DEM (> 10 m) might result in a slightly lesser designed network.
4.	Only OSM is supported for Streets (**NOT** Buildings or other inputs). Other open-access street or road sources can be available in a later version.
5.	For now, this plugin works well with UTM coordinate systems. For other coordinate systems, the outlet distance validation might raise issues. Support for the Geographic system are planned for a later version.


<br>

# OG_FLUSH (DE)

## Beschreibung
**OG_FLUSH** (**O**pen-access **G**IS-based **F**low **L**ayout for **U**rban **S**ewer **H**ydrodynamics) ist ein QGIS-Plugin. Es wurde entwickelt, um automatisch Kanalnetzstrukturen auf Basis von Open-Source-Geodaten zu generieren – idealerweise aus der Open-Access-Quelle **OpenStreetMap**. Die Ergebnisse dienen als Grundlage für die Erstellung hydrodynamischer Kanalnetzmodelle, wie zum Beispiel für das **Storm Water Management Model (SWMM)**.

Detaillierte Informationen zum Konzept und der Methodik finden Sie unter: https://www.mdpi.com/2073-4441/15/1/46.

Dieses Tool wurde im Rahmen des Projekts **KlimaKonform** entwickelt. Weitere Informationen dazu finden Sie hier: https://klimakonform.uw.tu-dresden.de.

⚠️ **Hinweis:** Dieses Plugin befindet sich noch in der Entwicklung (*Work in Progress*).

<br>

## Eingangsdaten (Inputs)
Die folgenden Eingangsdaten sind für dieses Plugin erforderlich:

| Parameter | Anforderung | Typ | Beschreibung | Quelle |
| --- | --- | --- | --- | --- |
| Untersuchungsgebiet | Erforderlich | ESRI Polygon Shapefile | Grenze des betrachteten Gebiets | Benutzerdefiniert |
| Auslass (Outlet) | Erforderlich | ESRI Point Shapefile | Einzelner Endpunkt des Netzes (z. B. Kläranlage oder Einleitungsstelle) | Benutzerdefiniert |
| Gebäude | Erforderlich | ESRI Polygon Shapefile | Gebäudegrundrisse innerhalb des Gebiets | Verschiedene (z. B. OSM, Google Open Buildings) |
| Straßen | Erforderlich | ESRI LineString Shapefile | OSM-basiertes Straßennetz zur Ausrichtung der Kanalisation | OSM |
| Digitales Geländemodell (DGM) | Erforderlich | Raster | Höhendaten des Geländes | Verschiedene (z. B. Stadtportale) |
| Bevölkerungsdichte | Optional | ESRI Point Shapefile | Bevölkerungsverteilung für die Mischwasserplanung | Verschiedene (z. B. OSM) |

<br>

## Vorbereitung
Bitte beachten Sie die folgenden Punkte bei der Vorbereitung der Eingabedateien:
1. Stellen Sie sicher, dass alle Eingangsdaten in einem **UTM-Koordinatensystem** vorliegen.
2. Stellen Sie sicher, dass die Daten für Gebäude, Straßen, Gelände und Bevölkerungsdichte das **gesamte Untersuchungsgebiet** abdecken. Dies kann durch einen Puffer (Buffer) um das Untersuchungsgebiet und anschließendes Ausschneiden der Daten sichergestellt werden.
3. Stellen Sie sicher, dass alle Plugin-Abhängigkeiten in QGIS verfügbar sind. Weitere Informationen finden Sie im Abschnitt **Externe Abhängigkeiten**.

<br>

## Externe Abhängigkeiten
OG.FLUSH benötigt die Python-Bibliotheken **NetworkX**, **NumPy** und **Pandas**. Diese sind nicht immer standardmäßig in jeder QGIS-Umgebung enthalten. Falls sie fehlen, müssen sie manuell installiert werden:

**Installation über die OSGeo4W Shell (empfohlen bei offizieller Installation):**
1. Suchen Sie im Windows-Startmenü nach "OSGeo4W Shell" und öffnen Sie diese.
2. Prüfen Sie mit folgendem Befehl, ob `pip` installiert ist:
   `python -m pip --version`
3. Falls nicht vorhanden, installieren Sie `pip`:
   `python -m ensurepip --upgrade`
4. Installieren Sie die benötigten Bibliotheken:
   `python -m pip install networkx numpy pandas`
5. Die Konsole lädt fehlende Pakete herunter; bereits vorhandene werden übersprungen.
6. Starten Sie QGIS nach Abschluss neu.

**Alternative: Installation über die QGIS-Python-Konsole:**
1. Gehen Sie in QGIS zu **Erweiterungen** → **Python-Konsole**.
2. Geben Sie die folgenden Zeilen nacheinander ein und bestätigen Sie jeweils mit **Enter**:
   ```python
   import pip
   pip install networkx numpy pandas
3. Starten Sie QGIS anschließend neu.

<br>

## Anleitung
1. **Plugin installieren:**
   a. Gehen Sie zu **Erweiterungen** → **Verwalten und Installieren...**
   b. Suchen Sie nach **OG.FLUSH**.
   c. Klicken Sie auf **Plugin installieren**.
2. Klicken Sie nach der Installation auf das Icon* in der Werkzeugleiste.
   *\*Aktuell sieht es aus wie ein blaues Netzwerk. Wir hoffen, eines Tages einen professionellen Designer einstellen zu können.*
3. Falls das Plugin nicht erscheint, aktivieren Sie es im Erweiterungs-Manager oder starten Sie QGIS neu.
4. Wählen Sie die Shapefiles aus dem Dropdown-Menü aus. Falls sie bereits in QGIS geladen sind, erscheinen sie automatisch; ansonsten nutzen Sie den **…** Button.
5. Wählen Sie die Bemessungsparameter gemäß lokaler Vorschriften. Weitere Infos erscheinen als Pop-up, wenn Sie mit der Maus über die Felder fahren (**Hover**).
6. Für ein **Mischsystem** aktivieren Sie das entsprechende Kontrollkästchen und geben Sie die Daten ein.
7. **Vernetzungsgrad (Meshness):** Wenn Sie zusätzliche Rohre (z. B. als Stauraum) hinzufügen möchten, geben Sie den Prozentsatz der im Hauptentwurf übersprungenen Verbindungen an.
8. Wählen Sie einen Ausgabeordner.
9. Klicken Sie auf den Button **"Run"**.
10. Keine Sorge, falls QGIS für einige Minuten "einfriert" – das Programm arbeitet im Hintergrund. Der Fortschrittsbalken hält Sie auf dem Laufenden.

<br>

## Annahmen und Einschränkungen
1. Alle Kanäle werden entlang (technisch gesehen: unter) den Straßen geplant.
2. Zur Dimensionierung der Rohre wird das **Zeitbeiwertverfahren** (Rational Method) verwendet.
3. Ein DGM mit geringer Auflösung (> 10 m) kann zu ungenaueren Netzentswürfen führen.
4. Aktuell wird nur **OSM** für das Straßennetz unterstützt (**NICHT** für Gebäude oder andere Inputs). Andere Quellen sind für spätere Versionen geplant.
5. Das Plugin arbeitet derzeit optimal mit **UTM-Koordinatensystemen**. Bei geografischen Koordinatensystemen kann es zu Fehlern bei der Validierung der Auslass-Distanz kommen. Eine Unterstützung dafür ist geplant.

## Authors/Autoren 
Diego Novoa Vazquez  
Julian David Reyes Silva  
Md Sifat Siddik  
  
All affiliated with,  
Urban Hydrology Research Group  
Institute for Urban and Industrial Water Management  
TU Dresden  


<br>

## Contact/Kontakt
diego.novoa_vazquez@tu-dresden.de  
md_sifat.siddik@tu-dresden.de  


<br>

## Important Links/Wichtige Links:
**Article:** Reyes-Silva, J. D., Novoa, D., Helm, B., & Krebs, P. (2023). An Evaluation Framework for Urban Pluvial Flooding Based on Open-Access Data. Water, 15(1), 46. https://doi.org/10.3390/w15010046  
**Sewer network meshness:** https://doi.org/10.2166/wst.2020.070  
**OpenStreetMaps:** https://planet.openstreetmap.org  
**SWMM:** https://www.epa.gov/water-research/storm-water-management-model-swmm
