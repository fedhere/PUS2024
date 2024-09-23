## Due Friday 27 at 11:59PM

# Slides
https://slides.com/federicabianco/pus_03 https://slides.com/federicabianco/pus_04


# Assigned Reading

[The earth is roung P < 0.05](https://www.iro.umontreal.ca/~dift3913/cours/papers/cohen1994_The_earth_is_round.pdf) By Jeff LEek and Roger Peng. https://slides.com/federicabianco/pus_03 https://slides.com/federicabianco/pus_04



# ASSIGNMENTS: You are encouraged to work in groups!! I advise you look for partners to work with on slack. If you need help finding a partner let me know.

## Assignment 1 P-value statistics


**Follow instructions in the [skeleton notebook](https://github.com/fedhere/PUS2024/blob/main/HW3/effectivenes_of_NYC_Post_Prison_Employment_Programs.ipynb))**

Follow the notebook instyructions. Note: the notebook includes images that are loaded in the version I prepared. DO NOT RUN THE CELLS OF CODE THAT LOAD THE IMAGES
you can remove those cells or leave them but not run them and then look at the relevant values in the orignial notebook

IMPORTANT: there is a function call that calculates the chi square. `from evalChisq import evalChisq`
You can either:

- remove that line of code and create your own evalChisq function based on the definition

- put the script evalChisq.py which is (now) in this repo into the directory where you are working and run the line of code that imports the function `from evalChisq import evalChisq`

    - this can be done by manually downloading the script from the repo and uploading it to colab (least good option because its not reproducible!)
    - you can use the terminal command `wget` to download it directly from the notebook. This makes this operation reproducible (so long as the link continues to exist)
   the command should look as follows: `!wget https://....` . Note: the exclamation mark indicated we are using a terminal, not a python command. The URL you should get from the repo but remember to get the _raw_ file. Similarly, the file will land on the colab folder where you are working (see image below)

<img width="657" alt="Screen Shot 2024-09-23 at 11 00 55 AM" src="https://github.com/user-attachments/assets/3499fdf0-7c0c-46e5-8e96-1d01e7fc2373">

## Assignment 2 Linear Regression

Follow the [skeleton notebook](https://github.com/fedhere/PUS2024/blob/main/HW3/instructions_Notebook_Linear_Regression___Water_Consumption.ipynb) which reproduces the analysis in  https://www.mdpi.com/2079-9276/8/3/156 . Take a look at the paper, its really well written! 
