# ImagePut

* Accepts many [inputs](https://github.com/iseahound/ImagePut/wiki/Input-Types-&-Output-Functions#input-types). 
* Standalone library.
* Easily understandable syntax. 
* Fast conversions.
* Highly robust code that has undergone extensive testing. 

## Documentation

* [Input Types & Output Functions](https://github.com/iseahound/ImagePut/wiki/Input-Types-&-Output-Functions)
* [Crop, Scale, & Other Flags](https://github.com/iseahound/ImagePut/wiki/Crop,-Scale,-&-Other-Flags)
* Chinese Documentation (中文) - [这里有一个中文版的使用教程](https://www.autoahk.com/archives/37246)

Projects using ImagePut:

* [PaddleOCR-AutoHotkey](https://github.com/telppa/PaddleOCR-AutoHotkey)

If you like this and want to see my other AutoHotkey libraries:

* [TextRender & ImageRender](https://github.com/iseahound/TextRender)

## So you want to convert an image?

But you don't how. That's okay because you can just do this:

    str := ImagePutBase64("cats.jpg")

or this

    ImagePutClipboard("https://example.com/cats.jpg")
    
or something like this:

    pStream := ImagePutStream([0, 0, A_ScreenWidth, A_ScreenHeight])
    
Working with images should be this easy. ImagePut has automatic type inference, meaning that it will guess whether the input is (1) a file (2) a website url or (3) a series of coordinates that map to the screen. This functionality enables the user to only memorize a single function for any possible input. For a full list of supported input types, click on the documentation link [here](https://github.com/iseahound/ImagePut/wiki/Input-Types-&-Output-Functions#input-types). For output types click [here](https://github.com/iseahound/ImagePut/wiki/Input-Types-&-Output-Functions#output-functions). 

Conversion between file formats is straightforward. 

    ; Saves a JPEG as a GIF. 
    ImagePutFile("cats.jpg", "gif")
    
Convert file formats and image types at the same time!

    ; Saves a JPEG as a base64 encoded GIF. 
    str := ImagePutBase64("cats.jpg", "gif")
    
There's also some weird functions like ```ImagePutCursor``` which lets you set anything as your cursor. Make sure you don't choose an extremely large image! 

Finally, there are several advanced features. The first is the ability to specify the [input type](https://github.com/iseahound/ImagePut/wiki/Input-Types-&-Output-Functions#input-types) directly. The second is [cropping](https://github.com/iseahound/ImagePut/wiki/Crop,-Scale,-&-Other-Flags#crop) and [scaling](https://github.com/iseahound/ImagePut/wiki/Crop,-Scale,-&-Other-Flags#scale) functionality. Third is use of ImageEqual() a function that can compare multiple inputs across different windows image data types!

    ; Declare input type as file.
    ImagePutWindow({file: "cats.jpg"})
    
    ; Scale 2x and crop 10% from each edge.
    ImagePutWindow({file: "cats.jpg", scale: 2, crop:["-10%", "-10%", "-10%", "-10%"]})
    
    ; Unknown image type declared as "image" to be cropped to 200x200 pixels. 
    ImagePutWindow({image: "cats.jpg", crop: [0, 0, 200, 200]})
    
    ; Compare a url to a file.
    MsgBox % ImageEqual("https://example.com/cats.jpg", "cats.jpg")
    
    ; Validate an image as an actual image.
    ImageEqual("cats.jpg")

## Design Philosophy

ImagePut is designed to be fast. However, because of the nature of ImagePut, it has been designed to be as fast as possible for many to many, one to many, and many to one operations. If you find that your script relies on a single conversion of one input type to one output type, then you are advised to look at the source code and see what you need. Single conversions can be optimized in ImagePut by declaring an input type as shown above. If you copy and paste my source code, you may get an additional small gain. For certain operations on Windows that involve specific conversions from one specific file format & input type to another, such as a PNG file in memory to hIcon, there do exist even faster operations that I have not implemented because they are extremely specific and rely on little known behavior. 

## Help and Support

Come visit the forum for any help, questions, suggestions, etc.

* v1 forum: https://www.autohotkey.com/boards/viewtopic.php?t=76301
* v2 forum: https://www.autohotkey.com/boards/viewtopic.php?t=76633

