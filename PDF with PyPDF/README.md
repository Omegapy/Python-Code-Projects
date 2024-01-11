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




