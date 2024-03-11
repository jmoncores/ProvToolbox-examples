# ProvToolbox-examples
Based on the 2.0.4 version.  
ProvToolbox project page http://lucmoreau.github.io/ProvToolbox/

### Basic Concepts
todo

### Conversion
Example of conversion between files.
```
package org.example.convert;

import org.openprovenance.prov.interop.Formats;
import org.openprovenance.prov.interop.InteropFramework;
import org.openprovenance.prov.model.Document;

import java.io.IOException;

public class Main {

    public static void main(String [] args) throws IOException {
            InteropFramework intF=new InteropFramework();
            Document document=intF.readDocumentFromFile("./resources/mention.json");
            intF.writeDocument("mention.jpeg", document, Formats.ProvFormat.JPEG);

    }
}
```
POM
```<dependencies>
        <dependency>
            <groupId>org.openprovenance.prov</groupId>
            <artifactId>prov-model</artifactId>
            <version>2.0.4</version>
        </dependency>
        <dependency>
            <groupId>org.openprovenance.prov</groupId>
            <artifactId>prov-interop</artifactId>
            <version>2.0.4</version>
        </dependency>
        (...)
```

+ InteropFramework: the interoperability framework that contains methods for writing and reading PROV documents to files or streams. It works based on media types and formats. The supported formats are: PROVN, PROVX, JSON, JSONLD, DOT, JPEG, PNG, SVG, PDF (available at org.openprovenance.prov.interop.Formats)
+ Document: the interface for a PROV Document.
+ readDocumentFromFile: in this case we are reading from a file.
  +  we could also read from a stream: readDocument(InputStream is, ProvFormat format);
  +  or from a URL. In this case, the Content-type HTTP header field is considered for the mime-type: readDocumentFromURL(String url).
+ writeDocument: writes the document in the desired format, in this case "jpeg". The Format specification could be omitted and serialization would occur according to the file extension.

