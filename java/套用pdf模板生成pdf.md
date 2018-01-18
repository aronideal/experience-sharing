
## 1. 准备pdf模板

使用 Adobe Acrobat 制作生成pdf，属性部分按需命名

## 2. 引入工具包

```xml
<dependency>
    <groupId>com.itextpdf</groupId>
    <artifactId>itextpdf</artifactId>
    <version>5.5.12</version>
</dependency>
```

## 3. 套用pdf模板，生成填充后的pdf

```java
public final class PdfTplUtils {

    public static void fillPdf(byte[] pdfTpl, byte[] ownerPassword, OutputStream pdfOutput, List<Properties> fields) throws IOException, DocumentException {
        PdfReader reader = new PdfReader(pdfTpl.clone(), ownerPassword);
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
        InputStream pdfTplInput = PdfTplUtils.class.getResourceAsStream("/template/test.pdf");
        ...
        byte[] pdfTpl = ...; // pdfTplInput -》 byte[] 略
        
        FileOutputStream pdfOutput = new FileOutputStream("D:\\out1.pdf");
        try {
            fillPdf(pdfTpl, null, pdfOutput, fields);
        } finally {
            pdfOutput.close();
        }
    }
}
```

