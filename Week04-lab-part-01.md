# การทดลอง วาดไดอะแกรมด้วย plantUML (2)


## 1. แผนภาพตามแนวคิด generalization abstraction

### 1.1 คลาสของสัตว์

#### 1.1.1 Mammals

- Dogs, cats, horses, duckbill platypuses, kangaroos, dolphins และ whales เป็นสัตว์เลี้ยงลูกด้วยนม
- ตัวอ่อนดื่มนมเป็นอาหาร และมีขนตามร่างกาย

#### วิเคราะห์คลาสหลัก Mammals 
Attributes 
- สีขน
- อายุ
- เพศ

Methods
 - กินอาหาร
 - เคลื่อนที่

``` plantuml
@startuml
class Mammal
{
    + color
    - age
    - gender
    + eat()
    + move()
}
@enduml
```

![](./Lab/Pictures/pict-01.png)


####  คลาสย่อย


``` plantuml
@startuml
class Dogs
class cats
class horses
class platypuses
class kangaroos
class dolphins
class whales
@enduml
```

![](./Lab/Pictures/pict-02.png)


#### การแสดงความสัมพันธ์ generalization

ทำได้โดยการใช้เครื่องหมายลูกศรสามเหลี่ยม หรือเขียนเป็นสัญลักษณ์ด้วย code ดังตัวอย่างด้านล่างนี้

``` plantuml
@startuml
"Base class" <|-- "Inherited class"
@enduml
```

### ตัวอย่างระบบคลาสของ mammals

``` plantuml
@startuml 
class Mammal
{
    + color
    - age
    - gender
    + eat()
    + move()
}

class Dogs
class cats
class horses
class platypuses
class kangaroos
class dolphins
class whales

Mammal <|-- Dogs
Mammal <|-- cats
Mammal <|-- horses
Mammal <|-- platypuses
Mammal <|-- kangaroos
Mammal <|-- dolphins
Mammal <|-- whales
@enduml
```

![](./Lab/Pictures/pict-03.png)


## แบบฝึกหัด 
ให้เขียนคลาสไดอะแกรมของหัวข้อต่อไปนี้ โดยใช้ plantuml


1. ให้นักศึกษาวาดไดอะแกรมของการ inheritance ของสัตว์ให้ครบทุกประเภท โดยเพิ่ม properties และ methods ได้ตามคำอธิบายหรือธรรมชาติของสัตว์ชนิดนั้นๆ 

    1.1  Birds เช่น เหยี่ยว ห่าน เป็ด ไก่ มีขน และเกิดจากไขที่มีเปลือกแข็ง ขนบนปีกและหาง จะทับซ้อนกันอยู่ ซึ่งทำให้โต้ลม และทำให้นกบินและร่อนลงได้

    1.2 Fish  เช่น ปลากัด ปลาทู ปลาแซลมอน เป็นสัตว์มีกระดูกสันหลัง อาศัยในน้ำ มี เหงือก (gills),  เกล็ด (scales)  และ ครีบ (fins)

    1.3 Reptiles (สัตว์เลื้อยคลาน)  เช่น จรเข้ งู กิ้งก่า เป็นสัตว์ที่มีเกล็ดบนผิวหนัง เป็นสัตว์เลือดเย็นและเกิดบนบก

    1.4 Amphibians (สัตว์ครึ่งบกครึ่งน้ำ) เช่น กบ เขียด อึ่งอ่าง เกิดในน้ำ เมื่อแรกเกิดจะหายใจด้วยเหงือกคล้ายปลา เมื่อโตขึ้นจะพัฒนาปอดขึ้นมาและอาศัยบนบกเป็นหลัก

    1.5 Arthropods เช่น กุ้ง ก้งกือ แมงมุม มด เป็นสัตว์ที่มีมากกว่า 4 ขา 
```plantuml
@startuml
class Animal {
    - has_skin: bool
}

class Bird {
    - has_feathers: bool
    - has_beak: bool
    - has_wings: bool
    - has_tail: bool
    + fly()
    + molt()
}

class Fish {
    - has_gills: bool
    - has_scales: bool
    - has_fins: bool
    + swim()
}

class Reptile {
    - has_scales: bool
    - is_cold_blooded: bool
    + crawl()
}

class Amphibian {
    - has_gills: bool
    - has_lungs: bool
    + swim()
    + jump()
}

class Arthropod {
    - has_exoskeleton: bool
    - number_of_legs: int
    + crawl()
}

Animal <|-- Bird
Animal <|-- Fish
Animal <|-- Reptile
Animal <|-- Amphibian
Animal <|-- Arthropod
@enduml
```
![image](https://github.com/tnpn2545/Week-04/assets/115066414/477a97d8-de54-40f2-8a5e-fb58fdcef61a)

2. ให้วิเคราะห๋และเขียนคลาสไดอะแกรม แสดงการสืบทอดของยานพาหนะ ทางบก ทางน้ำ และ ทางอากาศ
``` plantuml
@startuml
class Vehicle {
    - num_wheels: int
    - engine_size: float
    - max_speed: float
    + start_engine()
    + stop_engine()
}

class LandVehicle extends Vehicle {
    - ground_clearance: float
    + drive()
}

class Watercraft extends Vehicle {
    - boat_type: string
    - engine_count: int
    + float()
}

class Aircraft extends Vehicle {
    - aircraft_type: string
    - propulsion_system: string
    + fly()
}

Vehicle <|-- LandVehicle
Vehicle <|-- Watercraft
Vehicle <|-- Aircraft
@enduml
```
![image](https://github.com/tnpn2545/Week-04/assets/115066414/7efea7a5-cb93-4b00-a781-fa651378685e)

3. ให้ยกตัวอย่างประเภทของที่อยู่อาศัย ให้คำจำกัดความและแสดงคลาสไดอะแกรม
```plantuml
@startuml
class Dwelling {
    - address: string
    - num_rooms: int
    - num_bathrooms: int
    + get_address(): string
}

class SingleHouse extends Dwelling {
    - yard_size: float
    + maintain_yard()
}

class Townhouse extends Dwelling {
    - shared_walls: int
    + share_common_area()
}

class Condominium extends Dwelling {
    - floor_number: int
    - building_facilities: string[]
    + access_common_facilities()
}

class Apartment extends Dwelling {
    - num_units: int
    - unit_size: float
    + rent_unit()
}

class Villa extends Dwelling {
    - pool_available: bool
    - garden_size: float
    + enjoy_private_amenities()
}

Dwelling <|-- SingleHouse
Dwelling <|-- Townhouse
Dwelling <|-- Condominium
Dwelling <|-- Apartment
Dwelling <|-- Villa

@enduml
```
![image](https://github.com/tnpn2545/Week-04/assets/115066414/3640da6e-0ca2-4d7b-97d3-b98dbdaa0d35)

## 2. [แผนภาพตามแนวคิด Association abstraction](Week04-lab-part-02.md)


