-----------------------------------------------------------------------------------------------------------------------------
# PDF with PyPDF
-----------------------------------------------------------------------------------------------------------------------------

 Alejandro Ricciardi (Omegapy)  
 created date: 01/10/2024  

-----------------------------------------------------------------------------------------------------------------------------

Projects Description:  
How to read/write/manipulate PDF files using PyPDF.  
[PyPDF v3 and above Documentation](https://pypdf.readthedocs.io/en/stable/) 

Credit: 
[Control PDF with Python & PyPDF2](https://www.udemy.com/course/control-pdf-with-python-pypdf2) Udemy - Conny Soderholm  
The original code was substantially modified from PyPDF2 to PyPDF v3.17.4, to meet my requirements, and to add functionally to the program.

-----------------------------------------------------------------------------------------------------------------------------

Requirements:  
- [Python](https://www.python.org/)   
- [Jupyter Notebook](https://jupyter.org/) 

-----------------------------------------------------------------------------------------------------------------------------

Project map:
- The PyPDF PdfReader class (PdfReader.ipynb)
	Using the PyPDF [PdfReader](https://pypdf.readthedocs.io/en/stable/modules/PdfReader.html?highlight=PdfReader) class to read from a PDf file.

-----------------------------------------------------------------------------------------------------------------------------

My Links:   
- [GitHub](https://github.com/Omegapy)   
- [Facebook](https://www.facebook.com/profile.php?id=100089638857137)  
- [Twitter](https://twitter.com/RicciardiAlex)   
- [Instagram](https://www.instagram.com/alexomegapy/)  

-----------------------------------------------------------------------------------------------------------------------------
## PyPDF PdfReader Class
(PdfReader.ipynb)

-----------------------------------------------------------------------------------------------------------------------------

Projects Description:   
Using the PyPDF [PdfReader](https://pypdf.readthedocs.io/en/stable/modules/PdfReader.html?highlight=PdfReader) class to read from a PDf file.  

Class:
```
class pypdf.PdfReader(stream: Union[str, IO[Any], Path], strict: bool = False, password: Union[None, str, bytes] = None)
```

Parameters
- stream – A File object or an object that supports the standard read and seek methods similar to a File object. Could also be a string representing a path to a PDF file.

- strict – Determines whether the user should be warned of all problems and also causes some correctable problems to be fatal. Defaults to False.

- password – Decrypt PDF file at initialization. If the password is None, the file will not be decrypted. Defaults to None

Project map:
- Load and Read a PDF 
    - First method ``` with open(file_name, "rb") as pdf_file: ```
    - Second method ```pdf_reader = PdfReader("docs/WorkStation.pdf")```
- PDF files Metadata ```doc_info = pdf_reader.metadata```
    - Metadata (unscripted) 
    - Encrypted Metadata
- Fix for encrypted Metadata ```writer = PdfWriter().append_pages_from_reader(pdf_reader)```
- PDF Fields ```fields = pdf_reader.get_fields()```
- Page Document Layout ```pdf_reader.page_layout```
- Page Mode (Document outline) ```pdf_reader.page_mode```
- XPM Metadata ```xmp = pdf_reader.xmp_metadata```
- Get Text From Page - full page and lines ```xmp = pdf_reader.xmp_metadata``` and  
  ```for number, line in enumerate(full_page_text.splitlines()): ```


-----------------------------------------------------------------------------------------------------------------------------
## PyPDF PDF Manipulation  
(PyPDF PDF Manipulation.ipynb)

-----------------------------------------------------------------------------------------------------------------------------

Projects Description:   
Using PyPDF to manipulate PDF files.
- How to work with pages
- How to scale, rotate, crop, clip, and watermark pages
- How to split and join pages
- How to read a pdf to memory instead of having to write to disk

The [PageOject Class](https://pypdf.readthedocs.io/en/stable/modules/PageObject.html?highlight=add_transformation#the-pageobject-class) represents a single page within a PDF file. 

Typically this object will be created by accessing the ```pdf_reader_object.pages``` or ```pdf_writer_object.pages```, a list of all the pages, a page is a PageOject Class which is a subclass of the PdfReader and PdfWriter classes, but it is also possible to create an empty page with the ```create_blank_page()```.

Project map:
- Transformation Matrix 
    - Sheer Transformation x Axis To The Right ```page.add_transformation( (1,0,.5,1,0,0) )```
    - Sheer Transformation y Axis up ```page.add_transformation( (scale,0,0,scale,0,0) )```
    - Scaling Pages ```page.add_transformation( (scale,0,0,scale,0,0) )```
    - More Transformation Using the Transformation Matrix Method
- Rotated Page -```page.rotate(90)```
- Creating Blank Pages
    - Stand alone blank page ```blank_page = pages[0].create_blank_page(pdf=pdf_reader, width=None, height=None)```
    - Add a blank page at a particular index ```pdf_writer.insert_blank_page(None, None, 2)```
    - Add a blank page at the end of a PDF ```pdf_writer.add_blank_page()```
- Splitting PDFs
    - Splitting Documents in Half Or Thirds ```pdf_writer_0_to_5.append( pdf_reader, pages=(0, 5) )```
    - Splitting Documents by Individual Pages ```pdf_writer_even.append( pdf_reader, pages=[0,2,4,6,8,10] )```
- Merging PDFs ```for pdf in PDFList : pdf_writer_merged.append(pdf)```-
- PDF Boxes
    - Display Boxes Boundaries Functions
    - Format Page From A5 to A5 
- Clipping - Merge Pages ```page.merge_page(overlay_page)```
- Water Marking - Merge Pages ```page.merge_page(page_watermark, True, False)```
- Read PDF From Memory
- Decreasing PDF file size - PDF Compression ```page.compress_content_streams()```
