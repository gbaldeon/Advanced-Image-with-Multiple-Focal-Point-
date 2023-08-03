# Sitecore Fields

# Advance Image Sitecore
An image field with focus cropping option. Allows content authors to set focal point on images and cropping is done based on defined axes.

Package installs the field definition in Core database and setups templates and default thumbnails in Master database. This package also contains configuration and assembly files.

Complete installation instructions are available at:
https://inverseproportion.wordpress.com/2017/04/12/image-field-with-cropper-in-sitecore
https://sitecorecorner.wordpress.com/2019/06/29/advance-image-module-to-implement-focal-point-functionality-in-sitecore/

Advance Image field has following dependencies:
- Sitecore.Kernel
- Sitecore.Mvc
- ImageProcessor
- System.Drawing
- System.Web

# Module Details:
The Advance Image Focal Point using:
1.	Custom field called “Advance Image” created by extending the built-in Image field.
2.	Media Request Handler – checks for the additional custom parameters (querystring) for focus cropping. The details present at https://github.com/AmitKumar-AK/sitecore-fields/blob/master/src/Sitecore.Fields/Requests/CropMediaRequest.cs
3.	Image Processor – processes the image based on the passed parameters (querystring). The details present at https://github.com/AmitKumar-AK/sitecore-fields/blob/master/src/Sitecore.Fields/Processors/CropProcessor.cs
4.	The following items would be deployed into WebRoot and Sitecore using the Market place module at https://marketplace.sitecore.net/en/Modules/A/Advance_Image_Field.aspx:

<img src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-5.PNG" data-canonical-src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-5.PNG" style="max-width:100%;">

<img src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-6.PNG" data-canonical-src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-6.PNG" style="max-width:100%;">

5.	Now download the updated code from https://github.com/AmitKumar-AK/sitecore-fields which is Sitecore 9.1 compatible.
6.	Build the solution and deploy the latest assembly in to WebRoot\bin folder.
7.	Download the ImageProcessor.dll from https://www.nuget.org/packages/ImageProcessor and deploy to WebRoot\bin folder.
8.	Go to Sitecore\Core\ System\Field types\Advanced Field Types and select the Configure tab, press the Change button in the Template section, and select /sitecore/Common/Folder. 

With the help of above changes you will be able to see correct field options related to Image field in Content Editor when you will use custom <strong>“AdvanceImage”</strong> field in your custom Template:

<img src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-1.PNG" data-canonical-src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-1.PNG" style="max-width:100%;">

# How to use Advance Image Focal Point:
1.	To use the The Advance Image Focal Point module in your Project/Solution, first you have to install the module by following the steps mentioned in step <strong>“Module”</strong>.
2.	Create the custom template and use custom “Advance Image” field as a Field type. Please check the image template details at https://github.com/AmitKumar-AK/CT.SC/blob/master/src/Feature/PageContent/code/README.md
3.	Create the component which will access the filed and display on screen by passing the required dimensions.
Please check the component details at 
•	https://github.com/AmitKumar-AK/CT.SC/blob/master/src/Feature/PageContent/code/Controllers/PageContentController.cs
•	https://github.com/AmitKumar-AK/CT.SC/blob/master/src/Feature/PageContent/code/Models/Promo/PromoContentFactory.cs

    You can pass different dimension which defined at <strong>/sitecore/system/Modules/Advance Image  Module/Thumbnails/</strong> to access particular Focal Point image like 
<strong>Utilities.GetAdvancedImageUrl(Templates._PromoItem.Fields.AdvanceImage, item, 300,150);</strong>

Where Width is 150px and Height is 300px.
4.	The output of the image will be:
<img src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-2.PNG" data-canonical-src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-2.PNG" style="max-width:100%;">

The cshtml file code for the promo content present at https://github.com/AmitKumar-AK/CT.SC/blob/master/src/Feature/PageContent/code/Views/PageContent/PromoContent.cshtml

# How to add other dimensions:
1.	By default, following Thumbnail dimensions present at <strong>/sitecore/system/Modules/Advance Image Module/Thumbnails/</strong>:
•	150x300
•	200x180
•	350x80
•	80x80
2.	If you need to use another dimension for your requirement then you can add new dimension also like 
80x80 and it will start reflection on the content item where AdvanceImage field being used:

## New Thumbnail dimension:
<img src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-3.PNG" data-canonical-src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-3.PNG" style="max-width:100%;">

## Content Item: 

<img src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-4.PNG" data-canonical-src="https://github.com/AmitKumar-AK/sitecore-fields/blob/master/Notes/Sitecore%20Focal%20Point-4.PNG" style="max-width:100%;">

3.	To access newly created dimension in your code, you have to change the dimension, which you are passing in the code :
<strong>Utilities.GetAdvancedImageUrl(Templates._PromoItem.Fields.AdvanceImage, item, 80,80)</strong>;
Where Width is 150px and Height is 80px.


# Updates: Changes done for Sitecore 9.x
- .NET Framework 4.7.1
- Sitecore Version: Sitecore.NET 9.1.0 (rev. 001564)

# Credit:
A big thanks to Saad Ahmed Khan (https://twitter.com/saad_ahmed_khan) for creating the module and Khushboo Sorthiya (https://twitter.com/khush_Sorthiya) to provide details about experience editor improvements

# Reference:
- https://inverseproportion.wordpress.com/2017/04/12/image-field-with-focus-cropper-in-sitecore/
- https://sitecorecorner.wordpress.com/2019/06/29/advance-image-module-to-implement-focal-point-functionality-in-sitecore/


