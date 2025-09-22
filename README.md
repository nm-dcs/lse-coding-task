# **Coding Task**

### **Overview**

The purpose of this task is to help us better understand the code that you write. We know that development practices utilise AI-generated code, and we’re expecting you to use AI tooling as you do normally.

Define the code structure and implement it in line with best practices for your chosen programming language. **Please use Go or Python for this task**.

### **Expectations**

* Timebox this exercise to **under an hour**.
* Use Go or Python.
* We should be able to easily **build and run** your solution to validate the outputs.  
* Please share a link to a **public GitHub repository** with us containing your solution, or create a private GitHub repository and share access with GitHub users: **nm-dcs**, **jladbrook** and **AlexHandyNM**.

### **What we’re looking for**

* Well-structured, extendable, and maintainable code.
* Idiomatic code and style that matches the programming language.
* Demonstration of good development practices (e.g., error handling, clear separation of concerns).

### **Task Requirements**

Your task is to develop a command-line ETL (Extract, Transform, Load) tool that can extract data from the provided JSON structure, apply a set of transformations, and load the result into a CSV format.

#### **Input Data**

The tool should be able to read a JSON file with the following structure:

```json
{
  "torbayUuid": "40521e31-a215-497f-88a1-96833c2a610e",
  "torbayVersion": "1.41.0",
  "torbayHash": "33b171929ad59e9331f051de0fac2989d438f3f2",
  "result": {
    "customerId": "C01234",
    "customerName": "Nature Metrics UK Digital",
    "projects": [
      {
        "projectId": "PROJ01234",
        "runId": "ZG000001",
        "projectName": "Example Project Name",
        "projectDetails": {
          "projectStartDate": "12/31/2025",
          "countries": [
            "UNITED_KINGDOM"
          ]
        },
        "assays": [
          {
            "assayId": "Leray1",
            "assayName": "Invertebrates"
          }
        ],
        "features": [
          {
            "featureKey": "speciesdetector",
            "featureName": "Species detector"
          }
        ],
        "samples": [
          {
            "sampleId": "55191_3",
            "customerSampleId": "Rocky JunKyard A",
            "kitBarcode": "ASI-01-12448",
            "location": {
              "coordinates": "57.889304,-5.182286",
              "type": "Point"
            },
            "sampleCollectedDate": "13th January 2025",
            "sampleCollectedTime": "14:32",
            "sampleProcessedDate": "20th January 2025",
            "sampleProcessedTime": "14:32"
          },
          {
            "sampleId": "55191_2",
            "customerSampleId": "Rocky JunKyard B",
            "kitBarcode": "ASI-01-12449",
            "location": {
              "coordinates": "57.789304,-5.182286",
              "type": "Point"
            },
            "sampleCollectedDate": "14th January 2025",
            "sampleCollectedTime": "12:32",
            "sampleProcessedDate": "25th January 2025",
            "sampleProcessedTime": "12:32"
          }
        ]
      }
    ]
  }
}

```

#### **Expected Output**

The final output should be a CSV file written to standard output or a specified file path. It should contain a header row and one row for each sample, formatted as follows:

```
customerId,customerName,projectId,projectName,sampleId,customerSampleId,latitude,longitude,sampleCollectedDateTime,sampleProcessedDateTime,processingTimeDays
C01234,Nature Metrics UK Digital,PROJ01234,Example Project Name,55191_3,Rocky JunKyard A,57.889304,-5.182286,2025-01-13T14:32:00Z,2025-01-20T14:32:00Z,7
C01234,Nature Metrics UK Digital,PROJ01234,Example Project Name,55191_2,Rocky JunKyard B,57.789304,-5.182286,2025-01-14T12:32:00Z,2025-01-25T12:32:00Z,11

```

#### **CLI Behaviour**

The tool should accept the input file path as a command-line argument.

**Example Usage:** `./etl-tool --input /path/to/input.json`

The tool should handle basic errors, such as the input file not being found or containing invalid JSON, by printing a clear error message to the console.

