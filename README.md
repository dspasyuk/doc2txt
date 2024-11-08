Here's a README file for your module:
doc2txt

doc2txt is a Node.js module that extracts text from various document formats, including .txt, .doc, .docx, and .pdf files. It leverages multiple libraries to parse document contents and convert them into plain text, making it useful for applications that need to analyze or process document content programmatically.
Features

    Extracts text from:
        .txt, .py, .js, .sh, .md, .csv, .json files
        Microsoft Word .doc and .docx files
        PDF .pdf files
    Supports handling of nested XML structures in .docx files
    Built-in handling of unsupported file formats

Installation

Install doc2txt along with its dependencies:

npm install jszip xml2js word-extractor pdf-text-reader pdfjs-dist

Usage

First, import the doc2txt module and use its methods to read different document types.

import doc2txt from './path/to/doc2txt.js';

(async () => {
  const filePath = 'path/to/your/document.docx';
  const text = await doc2txt.extractTextFromFile(filePath);
  console.log(text);
})();

API
doc2txt.readTextFromTxt(filePath)

Reads plain text from a .txt file.

    Parameters:
        filePath (string): Path to the .txt file.
    Returns: (Promise<string>) Extracted text content.

doc2txt.readTextFromDoc(filePath)

Reads text from a .doc file using word-extractor.

    Parameters:
        filePath (string): Path to the .doc file.
    Returns: (Promise<string>) Extracted text content.

doc2txt.readTextFromDocx(filePath)

Reads text from a .docx file by extracting XML and parsing its structure.

    Parameters:
        filePath (string): Path to the .docx file.
    Returns: (Promise<string>) Extracted text content.

doc2txt.readTextFromPdf(filePath)

Reads text from a .pdf file using pdf-text-reader.

    Parameters:
        filePath (string): Path to the .pdf file.
    Returns: (Promise<string>) Extracted text content.

doc2txt.extractTextFromFile(filePath)

Determines the file extension and calls the appropriate method to extract text.

    Parameters:
        filePath (string): Path to the file.
    Returns: (Promise<string>) Extracted text content or an empty string if the format is unsupported.

Supported File Types

    .txt, .py, .js, .sh, .md, .csv, .json: Plain text files.
    .doc: Microsoft Word (binary format).
    .docx: Microsoft Word (XML format).
    .pdf: Portable Document Format.

Dependencies

    jszip: For handling .docx files.
    xml2js: For parsing XML content in .docx files.
    word-extractor: For extracting text from .doc files.
    pdf-text-reader: For extracting text from .pdf files.
    pdfjs-dist: For parsing PDF content.

Example

Here's an example of how to use doc2txt to read text from various file formats.

import doc2txt from './path/to/doc2txt.js';

(async () => {
  const filePaths = [
    'example.txt',
    'example.doc',
    'example.docx',
    'example.pdf'
  ];

  for (const filePath of filePaths) {
    const text = await doc2txt.extractTextFromFile(filePath);
    console.log(`Text from ${filePath}:\n`, text);
  }
})();

Error Handling

Each method handles errors by logging the error message and returning an empty string. Unsupported formats will trigger a warning message.
License

MIT License.
