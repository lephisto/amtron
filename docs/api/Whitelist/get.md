**Get Whitelist**
----

Retrieves Whitelist (aKa. Authorized RFID Tags).

* **URL**

  /Whitelist?DevKey=:devKey&Pin=:pin&State=:state

* **Method:**
  
  `GET`
  
*  **URL Params**

   **Required:**
 
   `devKey=[integer]`
   `pin=[integer] /* PIN2 */`              
   `State=[Read,Open,Alive,Close]`

* **Success Response:**
  
  * **Code:** 200 <br />
    **Content:** 
    
    ```
    {
      "RemEntries": [integer],   /* Remaining Entries (98 + 2 Master Uids) */
      {
        "Name": [String],        /* Name (if set with the App) */
        "Uid": [String],         /* RFID Uid */
        "Master": [boolean]     /* Is Master Tag? */
      }
    }
    ```
 
* **Error Response:**

  * **Code:** 403 FORBIDDEN

* **Notes:**

    * Read requests to the Whitelist have to be Opened prior reading with the **Open** State. The first State=open request does not return any Data, just a 200 if the Pin was OK.
    * Every Read requests returns 10 Records. Every subsequent Read Request returns the next 10 Records, until RemEntries is Zero. Subsequent Requests have to be issued within two seconds, otherwise the "Session" will Timeout. To keep it open, send subsequent State=alive every Second. To release the Lock send State=Close.

