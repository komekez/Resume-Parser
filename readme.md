## Setup
 The project is build on Flask app and following steps needs to be taken to run the application
 1. Install Flask usind the Flask documentation (https://flask.palletsprojects.com/en/2.3.x/installation/)
 2. Run the .py file, you will get errors for not have libraries installed.
 3. Install the libraries using the following command on terminal
    ```
    pip3 install lib_name
    ```
 4. Once the application runs successfully, test the project by running the following link on browser
    http://localhost:9090/
 5. If 'Hello World' is displayed than the application is running successfully


## Postman

Since the resume parsing api is a POST api, we need to use POSTMAN (software to test input and outputs of api) to check the API

### Inputs
Following needs to be used as input in postman
1. Change the request type to POST
2. Use the following url for parsing API (http://localhost:9090/getParsedData)
3. Use form-data for inputing the resume
4. In KEY input file and change the type to File
5. In Value add your resume

PyPDF2.errors.DeprecationError: PdfFileReader is deprecated and was removed in PyPDF2 3.0.0. Use PdfReader instead.


Initial Code : 1554ms, 1747ms, 1599ms, 1571ms, 1589ms
