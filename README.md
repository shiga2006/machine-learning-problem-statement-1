Project Overview
This application uses trained models to predict breast cancer (specifically classifying as malignant or benign) and cervical cancer (indicating positive or negative risk). Additionally, it includes a report analyzer feature to extract information from uploaded medical reports. Predictions are based on pre-defined features, and a user-friendly GUI built with Tkinter simplifies the process of interacting with the tool.

Features
Breast Cancer Detection: Input 27 features associated with breast cancer (e.g., radius, texture, symmetry) to receive a prediction on whether the tumor is likely malignant or benign.
Cervical Cancer Detection: Input various lifestyle and health factors to determine the risk of cervical cancer.
Symptom Bot: Placeholder feature for future integration of symptom-based health predictions.
Report Analyzer: Extract relevant medical metrics from uploaded PDF and DOCX reports.
Detailed Result Information: Each prediction includes an explanation and suggested next steps.
DEMO LINK - https://youtu.be/hBD7aOpYrqQ?feature=shared
problems faced:
1. File Handling and Compatibility Issues
Challenge: Handling multiple file types (PDF and DOCX) requires different libraries (PyPDF2 for PDFs and python-docx for DOCX files), which sometimes have limitations, such as text extraction errors or unsupported formats.
Solution: Test the analyze_report function with various PDF and DOCX formats. If a file doesn’t extract correctly, consider adding exception handling and providing a user-friendly message.
2. Boolean Query Parsing Complexity
Challenge: The filter_data function for Boolean queries is basic, handling only and, or, and not operators, and can be error-prone with complex or nested queries.
Solution: For a more sophisticated Boolean parser, you could use a library like pyparsing or consider building a recursive parser to handle more complex Boolean expressions accurately.
3. Large File Uploads and Memory Management
Challenge: Handling large files in Flask, especially when extracting text or loading data into a DataFrame, can lead to memory overload, especially on limited servers.
Solution: Set file size limits in Flask using MAX_CONTENT_LENGTH and implement pagination or chunking for large DataFrames. Additionally, set up logging to monitor memory usage for better management.
4. Concurrency and Asynchronous Requests
Challenge: Processing multiple uploads and large files can slow down the application if multiple users interact simultaneously, as Flask by default runs single-threaded.
Solution: Consider deploying with gunicorn for handling concurrent requests or using asynchronous file processing tools like Celery for background processing, which keeps the server responsive.
5. Data Validation and Security Risks
Challenge: Without input validation, there’s a risk of SQL injection or malicious file uploads that could harm the server.
Solution: Sanitize all file names using secure_filename (as you’ve done) and validate all user inputs to prevent harmful data from being processed. Use libraries like Flask-Limiter to prevent abuse and secure API routes.
6. User Experience and Error Handling
Challenge: Providing clear, actionable feedback on user errors (e.g., unsupported file types, extraction errors) and handling server errors gracefully.
Solution: Implement a robust error-handling mechanism that returns helpful messages to the user in the JSON response, along with logging errors for debugging.
