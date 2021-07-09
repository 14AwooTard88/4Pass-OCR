# Project Abandoned

I will no longer be working on this project mostly out of guilt. There is 1 million post per day so roughly 500k per day split between blue and orange board. Google's reCaptcha cost $1000 per 1M post so they proably end up paying google $500 / day just for captcha or $185k/year just for captcha. 1 less google engineer mean 3 more 4chan engineer. And maybe jannies will get paid this time.

# 4chan Captcha Bypass (OCR)

This repo only contains OCR. For cleaning/spliting or scraping/posting please refer to the 'Related' section

![Imgur](https://i.imgur.com/VWvyWuh.png)

## Related

For Cleaning/Spliting Captcha refer to:
https://github.com/14AwooTard88/4Pass-CleanSplit

For Scraping Captcha and posting refer to:
https://github.com/14AwooTard88/4Pass-Scrape


## Background
There is a new captcha that 4chan just recently adopted (July 5th). And supposedly it will help make it's security better or something. I don't know the reasoning for this sudden change.

However, what i do know is that new changes means new exploits. And as an autist, I cannot let this sit unexploited.

![4chan new captcha](https://i.imgur.com/SvYiJZi.png)


## Project Summary

In this project I'll show you how you can generate a *.traineddata* that can later be used in your Tesseract project.

## Tools
### Tesseract Ocr (4.0.0 rc3)
For this we'll use a slightly older version of Tesseract. You can try newer version tho i'm not sure if it will work

You can download 'tesseract-ocr-w32-setup-v4.0.0-rc4.20181024.exe' archived from:
https://digi.bib.uni-mannheim.de/tesseract/

![Imgur](https://i.imgur.com/1SEwoDU.png)

### JTessBoxEditor (Optional)
*You don't really need this unless you want create your own .trainneddata
Instructions are on the bottom if you want it* 

Download the ***jTessBoxEditor-2.3.1.zip***:
https://sourceforge.net/projects/vietocr/files/jTessBoxEditor/

We use this editor to train the data
![Imgur](https://i.imgur.com/JcyaSZn.png)

### QT Box Editor (Optional)
*You don't really need this unless you want create your own .trainneddata
Instructions are on the bottom if you want it* 

We'll use this to generate .box data 

This contains the fix if you can't open the stable release version: 
https://github.com/zdenop/qt-box-editor/releases/tag/v1.12rc1

![Imgur](https://i.imgur.com/t1qg6j6.png)

## Instructions (Simple)
1. Download the .zip file which contains "chan.traineddata" in the 'tessdata' folder. You don't need anything else (unless you want to train your own data, then instructions are below)

2. Copy 'chan.traineddata' to 'C:\Program Files (x86)\Tesseract-OCR\tessdata'

2. Open cmd and type:

```
    cd "C:\Program Files (x86)\Tesseract-OCR"

    tesseract "C:\Path\To\Captcha.png" "C:\Path\To\Output" -l chan
```

You should see this in the out.txt:

0_Clean.png (No clean, No Split): 

![Imgur](https://i.imgur.com/r1HLB4x.png)

0_Clean.png (Clean, No split): 

![Imgur](https://i.imgur.com/YtOqim1.png)

0_Split.png (Clean, Split): 

![Imgur](https://i.imgur.com/VWvyWuh.png)

As you can see, the **best result that the ones that are fully cleaned and has gap in between the letters**

## Instructions (Advanced)
The 'chan.traineddata' that was included was generated with realitively small dataset. To improve accuracy, it is best if you add your own dataset in addition to what was included.

1. **Create your datasheet.png**

Data sheet just contains grid the characters you want to train. Nothing too fancy. I include a 'chan.xcd' that you can open with Gimp if you would like to see it.

You can add your character here
![Imgur](https://i.imgur.com/Y3pu8jU.png)

2. Create new folder
It's very important that you put the .png you made inside a new folder
![Imgur](https://i.imgur.com/QU5tJad.png)



4.  **Creating .box file**
Drag and drop your .png into QT Box Editor
![Imgur](https://i.imgur.com/nnzPUEo.png)

Click Yes To generate .box data
![Imgur](https://i.imgur.com/IbrYFpL.png)

QT Editor Will Generate .box data automatically
![Imgur](https://i.imgur.com/2XWgCCZ.png)

Edit the letters to make sure it's correct
![Imgur](https://i.imgur.com/VWaGsPg.png)

Save it

![Imgur](https://i.imgur.com/lGNU0IA.png)

5. **Train your data**

**Open JTessBoxeditor (Make sure you have java installed)**

![Imgur](https://i.imgur.com/5qXotWF.png)

**Make sure you have the right input**
- 'Tesseract Executables' should point to "C:\Program Files (x86)\Tesseract-OCR\combine_tessdata.exe"
- 'Training Data' should point to your .box file
- 'Language' Should be the file name of your .box and .png 
- Set option to 'Train with Existing Box'
- Hit Run

![](https://i.imgur.com/GefClWb.png)

**It should take less than a second to train since there is very little dataset**
![](https://i.imgur.com/buZdZrs.png)

**It will generate a bunch of files but you can delete everything except the tessdata folder, .box and .png file. The only thing that matters is the .trainneddata**
![](https://i.imgur.com/MLNvdxH.png)

6. **Your Done!**
Now scroll back up and follow the **Instruction (Simple)** on how to use your *.traineddata*

