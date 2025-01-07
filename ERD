ERD

Client {
	id int pk
	first_name varchar
	last_name varchar
	email varchar
	phone varchar
	password varchar
	last_car int > Car_List.key
}

Service {
	id int pk
	service_name varchar
	price decimal
	duration int
	description text
}

Wash {
	id int pk
	location.X int
	location.Y int
	address varchar
}

Car_List {
	key int pk
	type varchar
	make varchar
	model varchar
	car_year int
}

Record {
	record_id int pk
	wash_id int > Wash.id
	service_id int > Service.id
	client_id int > Client.id
	record_date date
	record_time time
	car_key int > Car_List.key
}
