# Word Placeholder Replacer

This project demonstrates how to use docx4j to replace placeholders in a Word document with actual values.

## Installation

To use this project, you will need to have the following dependencies installed:

- [Java SE Development Kit](https://www.oracle.com/java/technologies/javase-downloads.html)
- [Docx4j](https://mvnrepository.com/artifact/org.docx4j/docx4j)
- [Jaxb](https://mvnrepository.com/artifact/org.glassfish.jaxb/jaxb-runtime/2.3.1)

This will create a `target` folder with the built `placeholder-replacer.jar` file.

## Usage

To use the Placeholder Replacer, follow these steps:

1. Create a Word document with placeholders in it, using the `<<placeholder>>` format.
2. Save the document as a `.docx` file.
3. Use the following code to replace the placeholders with actual values:

```java
import java.io.File;
import java.io.FileOutputStream;
import java.util.HashMap;

import org.docx4j.Docx4J;
import org.docx4j.openpackaging.exceptions.Docx4JException;
import org.docx4j.openpackaging.packages.WordprocessingMLPackage;
import org.docx4j.wml.MainDocumentPart;

public class PlaceholderReplacer {

    public static void main(String[] args) throws Docx4JException {
        
        // Load the template file
        WordprocessingMLPackage template = WordprocessingMLPackage.load(new File("template.docx"));
        
        // Get the main document part
        MainDocumentPart documentPart = template.getMainDocumentPart();
        
        // Define the values for the placeholders
        HashMap<String, String> values = new HashMap<>();
        values.put("<<FULL_NAME>>", "John Doe");
        values.put("<<ADDRESS>>", "123 Main Street");
        values.put("<<CITY>>", "Anytown");
        values.put("<<STATE>>", "CA");
        values.put("<<ZIP>>", "12345");
        
        // Replace the placeholders with actual values
        PlaceholderUtils.replacePlaceholders(documentPart, values);
        
        // Save the modified document
        template.save(new FileOutputStream(new File("output.docx")));
    }
}
```
4. Create a Word document with placeholders in it, using the `<<placeholder>>` format.
5. Save the document as a `.docx` file.
6. Use the following code to replace the placeholders with actual values: