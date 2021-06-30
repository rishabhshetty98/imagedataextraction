The function to be called is create_metasheet(folder,sheetname). 
This function takes the path of the folder in which the metadata excel sheet is to be created. It takes input as the path of the folder and the desired name for the metadata sheet.

create_metasheet(folder,sheetname) consists of two functions:
1) create_meta(folder,sheetname):
   It takes the same inputs as the create_metasheet function. A workbook is initialised with the respective column names using the openpyxl library. The function checks whether 
   the folder is full and starts looking for .jpg images. These images are read, resized and rotated using opencv. After each resize and rotate operation, the files are saved into temporary copies and converted
   into an openpyxl image object. Then the function meta(filepath) is called that extracts metadata from every image and saves it as a dictionary object. Then the image name, the resized 
   rotated image objects created earlier are appended to the excel sheet in the respectively initiated columns. The metadata which is the python dict object is converted to json format and added to the excel sheet
   as a string. All of these operations happen iteratively for every image. As soon as all the images have been processed, the workbook is saved.

2) clear(folder):
   This function is used to delete any copies formed during the image and data processing inside the folder so as to not waste disk space while processing. This function also takes 
   the desired folder as input.


Helper functions:
1) convert2dec(a):
   This function is used to convert the latitudinal and longitudinal values to decimal.

2) meta(filepath):
   As stated above, this helper function extracts metadata from the image and saves it as a python dict object. It takes image path as the input.
   Two python dictionaries are initiate, exif and gps. The PIL library is used to get exif data from the image and values are stored in exif dict.
   The GPS info in an image consists of a list of its own with multiple values. This function stores the GPS information of the image
   in gps dict. Both dict objects are then used to build the final python dictionary that consists of only the values required for the excel sheet.

 
 
Colab for source code: https://colab.research.google.com/drive/12rSrJl3Dw6gEcGq5_Ge41AqIfckoMa07?usp=sharing