PDF OCR Viewer
Overview
The PDF OCR Viewer is a web-based application designed to facilitate the viewing and searching of PDF documents using Optical Character Recognition (OCR) data. It allows users to upload PDF files and associated JSON files containing OCR data, visualize the PDFs, and search for specific words with bounding box overlays on the corresponding pages.
Features

PDF Upload and Display: Upload multiple PDF files and render them using PDF.js for accurate visualization.
OCR Data Integration: Upload JSON files containing OCR data to enable word-level search with bounding box coordinates.
Search Functionality: Search for words within the uploaded PDFs, with results displayed alongside confidence scores and page numbers.
Interactive Navigation: Navigate through search results with previous and next buttons, highlighting matches with bounding box overlays.
Zoom Controls: Adjust the zoom level of the PDF viewer for better readability.
Responsive Design: A three-panel layout with a file list, PDF viewer, and search results, optimized for usability and clarity.

Prerequisites

A modern web browser (e.g., Chrome, Firefox, Edge) with JavaScript enabled.
No server-side dependencies; the application runs entirely in the browser.
PDF files and corresponding JSON files with OCR data in the expected format.

JSON File Format
The JSON file containing OCR data must be an array of objects, each with the following properties:

document_name: String, the name of the PDF file (e.g., "sample.pdf").
word: String, the recognized word.
page_num: Number, the page number where the word appears.
bbox: Array of four numbers, representing the bounding box coordinates [x1, y1, x2, y2] in points (72 DPI) with a top-left coordinate system.
confidence: Number, the OCR confidence score for the word (0 to 1).

Example:
[
  {
    "document_name": "sample.pdf",
    "word": "example",
    "page_num": 1,
    "bbox": [100, 200, 150, 220],
    "confidence": 0.95
  }
]

Setup Instructions

Download the Application:

Save the pdf_ocr_viewer.html file to your local machine.


Host the File:

Option 1: Open the pdf_ocr_viewer.html file directly in a web browser by double-clicking it or using the browser's "Open File" option. Note that some browsers may restrict file uploads due to security policies when opened locally.

Option 2: Serve the file using a local web server for full functionality. For example, using Python:
python -m http.server 8000

Then navigate to http://localhost:8000/pdf_ocr_viewer.html in your browser.



Prepare Files:

Ensure you have PDF files and corresponding JSON files with OCR data ready for upload.



Usage Instructions

Upload Files:

In the left panel, click "Upload PDF Files" to select one or more PDF files.
Click "Upload JSON File" to select a JSON file containing OCR data.


Select a PDF:

In the left panel, click a PDF file from the list to display it in the center panel.


Search for Words:

In the right panel, enter a search query in the search box.
Results will appear below, showing the word, page number, and OCR confidence score.
Click a result or use the "Previous" and "Next" buttons to navigate through matches.
Matching words are highlighted with green bounding boxes on the PDF pages.


Zoom Controls:

Use the "+" and "−" buttons in the viewer header to zoom in or out (50% to 300%).



Notes

The application assumes OCR coordinates are in a top-left coordinate system at 72 DPI. If your OCR data uses a different coordinate system or DPI, you may need to adjust the OCR_COORDINATE_SYSTEM or OCR_DPI constants in the JavaScript code.
Ensure the document_name in the JSON file matches the uploaded PDF file names (case-insensitive, ignoring ".pdf" extension).
The application includes error handling for invalid JSON formats and bounding box coordinates, with warnings displayed in the search panel.

Limitations

Large PDF files or extensive OCR data may impact performance due to client-side rendering.
The application relies on the browser's file API, which may have restrictions when run locally without a web server.
No server-side processing is included; all functionality is client-side.

Dependencies

PDF.js: Version 3.11.174, loaded via CDN for PDF rendering.
No additional server-side dependencies are required.

Troubleshooting

PDF Not Loading: Ensure the PDF file is valid and not corrupted. Check browser console for errors.
Search Results Not Showing: Verify that the JSON file is correctly formatted and that the document_name matches the PDF file name.
Bounding Boxes Misaligned: Confirm that the OCR coordinates match the expected DPI and coordinate system. Adjust OCR_DPI or OCR_COORDINATE_SYSTEM if needed.

License
This project is provided as-is for educational and personal use. No warranty is implied or provided.