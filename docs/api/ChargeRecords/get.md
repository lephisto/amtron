**Get ChargeRecords**
----

Retrieves information about Charging Sessions.

* **URL**

  /ChargeRecords?DevKey=:devKey&Start=:start&End=:end&State=:state

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `devKey=[integer]`
   `Start=[integer]`
   `End=[integer]`
   `State=[Read,Open,Alive,Close]`

* **Success Response:**
  
  * **Code:** 200 <br />
    **Content:** 
    
    ```
    {
      "RemEntries": [integer],   /* Number of Sessions in between Start and End */
      {
        "Start": [integer],      /* Starttime in Unixtime */
        "Stop": [integer],       /* Endtime in Unixtime */
        "ChrNr": [integer],      /* Charge Amount in Wh */
        "ChrCosts": [integer],   /* Chargecosts  */
        "Uid": [String]          /* RFID Uid  */
      }
    }
    ```
 
* **Error Response:**

  * **Code:** 403 FORBIDDEN

* **Notes:**

    * Read requests to the Chargerecords have to be Opened prior reading with the **Open** State.
    * Every Read requests returns 10 Records. Every subsequent Read Request returns the next 10 Records, until RemEntries is Zero. Subsequent Requests have to be issued within two seconds, otherwise the "Session" will Timeout. To keep it open, send subsequent State=alive every Second. To release the Lock send State=Close.
