
```java
public final class TemplateUtils {

    public static void fillPdf(URL templateURL, byte[] ownerPassword, OutputStream pdfOutput, List<Properties> fields) throws IOException, DocumentException {
        PdfReader reader = new PdfReader(templateURL, ownerPassword);
        PdfStamper stamper = new PdfStamper(reader, pdfOutput);

        AcroFields acroFields = stamper.getAcroFields();
        
        for (Properties field : fields) {
            acroFields.setField(field.getProperty("name"), field.getProperty("value"), field.getProperty("display"));
        }

        stamper.setFormFlattening(true);
        stamper.close();
        reader.close();
    }

    public static void main(String[] args) throws IOException, DocumentException {
        List<Properties> fields = new ArrayList<Properties>();
        URL url = TemplateUtils.class.getResource("/template/test.pdf");
        
        FileOutputStream pdfOutput = new FileOutputStream("D:\\out1.pdf");
        try {
            fillPdf(url, null, pdfOutput, fields);
        } finally {
            pdfOutput.close();
        }
    }
}
```

