# Performance Testing Assignment

##  Objective
The objective of this assignment is to validate both functional and non-functional requirements of the Category API using a performance testing tool and analyze system behavior under controlled load conditions.

##  API Details
**Endpoint:**
https://api.tmsandbox.co.nz/v1/Categories/{CategoryID}/Details.json?catalogue=false

**Test Data (Category IDs):**
6327, 6328, 6329, 6330, 6331, 6332, 6333, 6334, 6335, 6336

**Test Data File Location in Repository**:CategoryId.csv in the Repo

If you want to run the script, ensure:
- The Category IDs are read from the above file
- File path is correctly configured in the test script

---

## ✅ Functional Requirements Implementation

The test script performs the following validations:

- ✅ HTTP Response Status Code is **200**
- ✅ Category ID in response matches request
- ✅ Response field `"CanRelist"` is **true**

---

## ✅ Data Extraction Requirement

The script extracts the following fields:

- Category ID  
- Name  
- Path  
- Promotion ID  
- Price  

📁 **Output File:**- output.csv in the repo

## ✅ Non-Functional Requirements Implementation

| Requirement | Expected | Implemented |
|------------|----------|------------|
| VUsers | Half of Category IDs (10 → 5) | ✅ 5 Threads |
| Ramp-up | 1 VUser/sec | ✅ Achieved |
| Test Duration | 1-minute steady state | ✅ Achieved |
| API Calls | 10 total calls | ✅ Achieved |
| SLA | 90% requests < 500 ms | ❌ Not Met |

---

## ⚙️ Test Execution (Non-GUI)

The test is executed in **non-GUI mode** as required.
Sample command (need to update the paths)
Jmeter command: .\jmeter -n -t "Assignment.jmx" -l "results.jtl" -e -o "report"


**Performance Test Observations and Recommendations:**
No request failures (0% error rate)
API is stable under defined load
The 90 percentile is not within SLA of 500ms and hence needs to investigated.
Response times are inconsistent as the min response time is 353 ms and max response time is 1.717 sec irrespective of the payload.
Detailed Report in the repository: 

