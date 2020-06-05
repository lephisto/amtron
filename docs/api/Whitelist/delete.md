**Delete Whitelist**
----

Deletes an entry from the Whitelist (aKa. unauthorize RFID Tags).

* **URL**

  /Whitelist?DevKey=:devKey&Pin=:pin&Uid=:Uid

* **Method:**
  
  `DELETE`
  
*  **URL Params**

   **Required:**
 
   `devKey=[integer]`
   `pin=[integer] /* PIN2 */`
   `Uid=[integer] /* Uid to delete`
* **Headers**
  **Required:**
  `Accept: 'application/json'`
  `Content-Type: 'application/json; charset=utf-8'`


* **Success Response:**
  
  * **Code:** 200 <br />
  
* **Error Response:**

  * **Code:** 403 FORBIDDEN

* **Notes:**

    * Set headers properly, otherwise the Webserver will `500`

