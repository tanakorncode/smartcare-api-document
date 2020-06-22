# smartcare-api-document

## TABLE OF CONTENTS
- [รายชื่อแพทย์ตามตารางเวลาออกตรวจ](#รายชื่อแพทย์ตามตารางเวลาออกตรวจ)

### รายชื่อแพทย์ตามตารางเวลาออกตรวจ

* **URL**

  `https://smartcare.egat.co.th/api/queue/v1/kiosk/doctors`

* **Method:**
 
  `GET`

* **Headers:**

   ```yaml
   {
     accept: 'application/json'
   }
   ```

*  **URL Params**

   **Required:**
   
   ```yaml
   {
     service_group_id: [integer],
     service_id: [integer]
   }
   ```
   
   | Params  | Description |
   | ------------- | ------------- |
   | service_group_id  | ไอดีกลุ่มงานบริการ  |
   | service_id  | ไอดีงานบริการ  |
   
  
 * **Data Params**

      None

 * **Success Response:**

   ```yaml
   {
     "success": true,
     "message": "ok",
     "data": {
        doctor_name: "พญ.นงนุช อังกุราภินันท์",
        doctor_id: 1,
        doctor_eid: "67504",
        prename: "พญ.",
        first_name: "นงนุช",
        last_name: "อังกุราภินันท์",
        assign_qty: 20,
        total_qty: 40,
        isFull: false,
        count_queue: 1,
        booking_status: "receive",
        assign_available_qty: 19,
      }
   }
   ```
 
* **Error Response:**

   * **Example:** <br />
   ```yaml
   {
     "statusCode": 400,
     "name": "Bad request",
     "message": "invalid params"
   }
   ```

* **For example call:**

  commands:
  ```
  curl -X GET "https://smartcare.egat.co.th/api/queue/v1/kiosk/doctors?service_group_id=1&service_id=6" -H "accept: application/json"
  ```

   OR

  axios Document [https://github.com/axios/axios](https://github.com/axios/axios)
  ```js
  const axios = require('axios');

  axios.get('/queue/v1/kiosk/doctors', {
    baseURL: 'https://smartcare.egat.co.th/api',
    params: {
      service_group_id: 1, // ไอดีกลุ่มงานบริการ
      service_id: 6 // ไอดีงานบริการ
    }
  })
  .then((response) => {
     console.log(response);
  })
  .catch((error) => {
     console.log(error);
  });
  ```

* **Notes:**

  **รายละเอียด:**
    | Filed Name  | Description |
    | ------------- | ------------- |
    | doctor_name  | ชื่อแพทย์  |
    | doctor_id  | ไอดีอ้างอิงแพทย์ (Queue)  |
    | doctor_eid  | ไอดีอ้างอิงแพทย์ (iMed)  |
    | prename  | คำนำหน้า  |
    | first_name  | ชื่อ  |
    | last_name  | นามสกุล  |
    | assign_qty  | จำนวนคิวที่ระบุแพทย์ได้  |
    | total_qty  | จำนวนคิวทั้งหมดที่รับ  |
    | isFull  | สถานะคิวเต็ม (Boolean)  |
    | count_queue  | จำนวนคิวที่มีอยู่ในระบบ(เฉพาะของแพทย์)  |
    | booking_status  | สถานะการจองคิว `receive: ยังรับจอง`, `full: คิวเต็ม`  |
    | assign_available_qty  | จำนวนคงเหลือที่ระบุแพทย์ได้  |
