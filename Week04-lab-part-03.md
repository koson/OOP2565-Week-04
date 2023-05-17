# การทดลอง วาดไดอะแกรมด้วย plantUML (2)
## การวาดไดอะแกรมที่มีองค์ประกอบมากขึ้น

ให้นักศึกษาพิจารณาวาด uml diagram ของ code ต่อไปนี้ในกระดาษ โดยยังไม่ต้องใช้ plantuml จากนั้นให้ไปวาดใน  plantuml แล้วเปรียบเทียบผลที่ได้ว่าตรงตามที่คิดหรือไม่


1. 

``` plantuml
@startuml
"Football team" "1..1" *-- "12..20" "Player"
"Football team" "1..1" *-- "1..2" "Coach"
"Coach" - "Player": > teach
@enduml
```

![image](https://user-images.githubusercontent.com/115066414/235317048-848af99b-ab55-41e1-a667-189f532a050e.png)
![582211A8-CC65-4C99-8E13-92452B5DAAD8](https://github.com/tnpn2545/Week-04/assets/115066414/00bf8390-d7dd-41ee-ad08-f31c57f13331)


2. 

``` plantuml
@startuml
class Student
{
  - name
  - ID
  - GPA
  + enrollSubject()
  + takeExamination()
}

class Subject
{
  - name
  - capacity
  - studytime
  + enrollStudent()
  + exam()
}

class Professor
{
  - name
  - emailAddress
  - instructs()
}

Student "10..40" - "0..1" Subject : > enrolled in
Subject "1" - "1..3 "Professor : < instructs
@enduml

```

![image](https://user-images.githubusercontent.com/115066414/235317073-c4ea3189-0243-473b-9f38-a1e9966fdbb2.png)
![9099C4EB-858A-41B5-A987-EF3F0E10F2D5](https://github.com/tnpn2545/Week-04/assets/115066414/fe29e69e-db35-47d8-9153-8771fcb4cc4d)


3. 


``` plantuml
@startuml
class Clock
{
 - time
 + getTime()
 + incrementTime()
}

class Display
{
 - time
 + initTime()
 + setTime()
 + displayTime()
}

class HistoryCall
{
 - count
 + call()
 + answer()
} 

class Call
{
 - callDuration
 + getDuration()
} 

class OutgoingCall
{
  - number
  + Dial()
}

class IncomingCall
{
  - number
  + Answer()
}

MobilePhone "1" *-- "1" Clock
MobilePhone "1" *-- "1" Display
MobilePhone "1" *- "1" HistoryCall
HistoryCall "1" *-- "n" Call
Call <|-- IncomingCall
Call <|-- OutgoingCall
OutgoingCall "1" -- "1..12" DialPad : > use
IncomingCall "1" -- "1..2" AnswerButton : > use
DialPad -|> Keypad 
Keypad <|- AnswerButton
@enduml
```
![image](https://user-images.githubusercontent.com/115066414/235317097-111e1f44-6236-4fb9-bb08-6aa2bac207b7.png)
![2AB9853C-B0F3-4440-BD11-ECB7EDAC7327](https://github.com/tnpn2545/Week-04/assets/115066414/b01b5d25-d0e7-447e-bd01-c11be6214d9c)


### จบการทดลองและแบบฝึกหัด
