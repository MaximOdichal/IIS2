### 3. ERD
![image](https://github.com/user-attachments/assets/f82b4368-7d8c-4fe9-9a8f-8bc74ad0b688)


<details>
  <summary>Код ERD</summary>
  
```plaintext

Table Client {
  id int [pk]
  first_name varchar
  last_name varchar
  email varchar
  phone varchar
  password varchar
  last_car int [ref: > Car.key]
}

Table Wash {
  id int [pk]
  name varchar
  locationX int
  locationY int
  address varchar
  rating float
  contact_phone varchar
}

Table Service {
  id int [pk]
  name varchar
  description text
  price decimal
  duration int
}

Table Car {
  key int [pk] 
  type varchar 
  make varchar 
  model varchar 
  car_year int
}

Table Record {
  id int [pk]
  client_id int [ref: > Client.id]
  wash_id int [ref: > Wash.id]
  service_ids int[] [ref: > Service.id]
  car_key int [ref: > Car.key]
  record_datetime datetime
  status varchar
  total_price decimal
}

Table Payment {
  id int [pk]
  record_id int [ref: > Record.id]
  payment_datetime datetime
  amount decimal
  payment_status varchar
  payment_method varchar
}

Table Support {
  support_id int [pk]
  client_id int [ref: > Client.id]
  request_topic varchar
  issue_description text
  created_at datetime
  request_status varchar
}

```

</details>
