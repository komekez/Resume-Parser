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

Since the resume parsing api is a POST api, we need to use POSTMAN (software to test input and outputs of api to check the API

### Inputs
Following needs to be used as input in postman
1. Change the request type to POST
2. Use the following url for parsing API (http://localhost:9090/getParsedData)
3. Use form-data for inputing the resume
4. In KEY input file and change the type to File
5. In Value add your resume

### Outputs
Following is the output of the request
1. The output is a JSON response with key-value pair with parsed data
2. The data is parsed from the input resume


## Optimization
The first noticable thing in the original version of the script is long functions and repeatative code which is not a good coding structure as it not only makes code hard to read but only compilation and runtime increases

When tested initially using postman script, the average time for parsing the resume is around 2.82 seconds. Following steps has been taken to optimize the code in the limited amount of time given

1. Breaking the code into smaller functions, overall pdf_function is broken down into pdf_table, pdf_non_table and pdf_function where new functions has a specific processing to perform and hence reduces the size of the function making function more readable and also reduces the number of statements
2. There were multiple instances where the variable is first performs mathematical operation and than a function is called. Instead of using using the above mentioned structure, it is changed to formated where the mathematical operation is performed inside the function, which makes it chained function thus reducing operation time
3. Removal of unwanted varaible. Multiple unwanted variable were found in the code which was than removed from the code
4. If-else statement achietecture changed to reduce the ladder structure and line of code for runtime, also at multiple instances variable type is changed for easy processing 

## Feature Added
There were multiple data which is not parsed by the API, with the limited time, I added the following 3 features to be tested
1. Parsing of Skills : Function get_skills added which checks the labels like "SKILLS", "TECHNICAL SKILLS", etc for fetch the skills and append it in he dictionary
2. Parsing of Academic Projects : Function get_academic_projects added which checks the labels like "PROJECTS", "ACADEMIC PROJECT", etc for fetch academic project and append over the output
3. Parsing of Languages : In the similar fashion of above, Languages known by the user is also parsed using "LANGUAGES" label and append in output

<bold> After performing optimization and feature addition the script is tested again and the average runtime is in between 2.72 seconds </bold>

## Further optimization intuition

The other idea I had to further optimize the code is to use parallel processing. The intuition was to use Pyppeteer wrapper and open multiple nodes of the same resume and all the nodes should parse their own section, acting as a thread for their own section of the resume. Once they parse their section, they should send the data to the main function which created the thread and kill the thread. Once the excution of all the created threads is processed, they we can kill all the threads and return the data. 

Such kind of structures are very useful for fast processing of the data as they are capable of multiprocessing. But takes more time is designing such structure

