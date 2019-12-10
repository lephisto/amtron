**Get Statistics**
----

Retrieves Statistics from Wallbox (Day/Week/Month/Hyear/Year/Annual).

* **URL**

  /Statistics/[Day,Week,Month,Hyear,Year,Annual]?DevKey=:devKey

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `devKey=[integer]`

* **Success Response:**
  
  * **Code:** 200 <br />
    **Content for [Week,Month,Hyear,Year] :** 
    
    ```
    {
      "ChrNr": [integer],        /* Amount of Wh */
      "HybridNrg": [integer], 
      "Solar": [integer],        /* Percentage charged from Solar */
      "Tariff1": [integer],      /* Percentage charged at Main Tariff */
      "Tariff2": [integer],      /* Percentage charged at Off-peak Tariff */
      "Hybrid": ??,
      "ChgCosts": [integer],     /* Accumulated Costs */
      "HybridCosts": ??,
    }
    ```
    **Content for [Day,Week,Month,Hyear,Year] :** 
    
    ```
    {
      "ChrNr": [integer],        /* Amount of Wh */
      "HybridNrg": [integer], 
      "Solar": [integer],        /* Percentage charged from Solar */
      "Tariff1": [integer],      /* Percentage charged at Main Tariff */
      "Tariff2": [integer],      /* Percentage charged at Off-peak Tariff */
      "Hybrid": ??,
      "ChgCosts": [integer],     /* Accumulated Costs */
      "HybridCosts": ??,
      "AvgCosts": [integer],     
      "FixCosts": ??,            
      "OldCosts": ??,            
      "KmDiff": ??,              
    }
    ```
    **Content for [Annual] :** 
    
    ```
    {"Years": [
        {
          "ChrNr": [integer],        /* Amount of Wh */
          "HybridNrg": [integer], 
          "Solar": [integer],        /* Percentage charged from Solar */
          "Tariff1": [integer],      /* Percentage charged at Main Tariff */
          "Tariff2": [integer],      /* Percentage charged at Off-peak Tariff */
          "Hybrid": ??,
          "ChgCosts": [integer],     /* Accumulated Costs */
          "HybridCosts": ??,
          "AvgCosts": [integer],     /* not on Day: Average Costs */
          "FixCosts": ??,            /* not on Day */
          "OldCosts": ??,            /* not on Day */
          "KmDiff": ??,              /* not on Day */
        },
        {
          "ChrNr": [integer],        /* Amount of Wh */
          "HybridNrg": [integer], 
          "Solar": [integer],        /* Percentage charged from Solar */
          "Tariff1": [integer],      /* Percentage charged at Main Tariff */
          "Tariff2": [integer],      /* Percentage charged at Off-peak Tariff */
          "Hybrid": ??,
          "ChgCosts": [integer],     /* Accumulated Costs */
          "HybridCosts": ??,
          "AvgCosts": [integer],     /* not on Day: Average Costs */
          "FixCosts": ??,            /* not on Day */
          "OldCosts": ??,            /* not on Day */
          "KmDiff": ??,              /* not on Day */
        }
        ...
      ]
    }
    ```
 
* **Error Response:**

  * **Code:** 403 FORBIDDEN

* **Notes:**

