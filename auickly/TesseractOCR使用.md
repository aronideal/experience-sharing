
## 安装tesseract命令（以WIN环境为例）

[tesseract-ocr-setup-4.00.00dev.exe](http://digi.bib.uni-mannheim.de/tesseract/tesseract-ocr-setup-4.00.00dev.exe)

## 识别图片内容

    tesseract.exe --tessdata-dir [traineddata文件的所在目录] -l [语言文件名] [源图片文件路径] [输出路径]

如：

    CMD> tesseract.exe --tessdata-dir D:\tesseract\tessdata-dir -l chi_sim "C:\Users\Administrator\Desktop\source.jpg" D:\tesseract-out

## 命令使用帮助

```
Usage:
  tesseract.exe --help | --help-psm | --help-oem | --version
  tesseract.exe --list-langs [--tessdata-dir PATH]
  tesseract.exe --print-parameters [options...] [configfile...]
  tesseract.exe imagename|stdin outputbase|stdout [options...] [configfile...]

OCR options:
  --tessdata-dir PATH   Specify the location of tessdata path.
  --user-words PATH     Specify the location of user words file.
  --user-patterns PATH  Specify the location of user patterns file.
  -l LANG[+LANG]        Specify language(s) used for OCR.
  -c VAR=VALUE          Set value for config variables.
                        Multiple -c arguments are allowed.
  --psm NUM             Specify page segmentation mode.
  --oem NUM             Specify OCR Engine mode.
NOTE: These options must occur before any configfile.

Page segmentation modes:
  0    Orientation and script detection (OSD) only.
  1    Automatic page segmentation with OSD.
  2    Automatic page segmentation, but no OSD, or OCR.
  3    Fully automatic page segmentation, but no OSD. (Default)
  4    Assume a single column of text of variable sizes.
  5    Assume a single uniform block of vertically aligned text.
  6    Assume a single uniform block of text.
  7    Treat the image as a single text line.
  8    Treat the image as a single word.
  9    Treat the image as a single word in a circle.
 10    Treat the image as a single character.
 11    Sparse text. Find as much text as possible in no particular order.
 12    Sparse text with OSD.
 13    Raw line. Treat the image as a single text line,
                        bypassing hacks that are Tesseract-specific.
OCR Engine modes:
  0    Original Tesseract only.
  1    Neural nets LSTM only.
  2    Tesseract + LSTM.
  3    Default, based on what is available.

Single options:
  -h, --help            Show this help message.
  --help-psm            Show page segmentation modes.
  --help-oem            Show OCR Engine modes.
  -v, --version         Show version information.
  --list-langs          List available languages for tesseract engine.
  --print-parameters    Print tesseract parameters.
```

