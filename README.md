# kml2xml
Convert KML/KMZ to CSV, GCCS OVL (overlay) xml format or Command Web Effort xml format

Download the zipped jars: https://github.com/mdudel/kml2xml/blob/master/kml2xml.zip

Unzip kml2xml.zip.

To run:

java -jar "C:\Kml2Xml\dist\Kml2Xml.jar"

        Options
                ? or help: Print this message
                IN=path/to/input/filename (required)
                OUT=path/to/output/filename (optional)
                TITLE=TITLE OF EFFORT/OVERLAY (optional, use quotes if the title has spaces)
                FORMAT=the output schema, default is MNVR XML, use OVL to obtain GCCS-J OVL [MNVR,OVL](optional)

Example:

java -jar "C:\Kml2Xml\dist\Kml2Xml.jar" IN=C:\KML\Test.kml

java -jar "C:\Kml2Xml\dist\Kml2Xml.jar" IN=C:\KML\Test.kml OUT=C:\CMDWEB\Test.xml TITLE="TEST KML EFFORT" FORMAT=MNVR

java -jar "C:\Kml2Xml\dist\Kml2Xml.jar" IN=C:\KML\Test.kml OUT=C:\CMDWEB\Test.ovl TITLE="TEST KML OVERLAY" FORMAT=OVL

To use in code (see Kml2Xml.java https://github.com/mdudel/kml2xml/blob/master/src/kml2xml/Kml2Xml.java ):


                File fin = new File("pathToFile.kml");                
                
                DocumentBuilderFactory dbf = DocumentBuilderFactory.newInstance();
                dbf.setNamespaceAware(true); 
                DocumentBuilder db = dbf.newDocumentBuilder();
                Document doc = db.parse(fin);
                
                Features features = new Features(doc);
                features.setTitle("Name Of Overlay or Effort");
                
                String gccsOvl = features.getOvlXml();
                String commandWebEffort = features.getMnvrXml();
                String csvWithHeader = features.getCsvHeader() + features.toCsv();
                String plainCsv = features.toCsv();
                
                
                





