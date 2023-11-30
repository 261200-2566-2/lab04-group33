# lab4 - object oriented programming

minimalist rpg game ที่สามารถ run และเล่นใน console ได้เลย รูปแบบเกมจะเล่นสองคนโดยมีclass knight และ archer ที่มีสกิลแตกต่างกันให้เลือกในตอนเริ่มเกม ในแต่ละ turn เราจะสามารถโจมดีและใช้สกิลอย่างละครั้ง ฝ่ายชนะจะเป็นฝ่ายที่ทำให้ hp ของอีกฝ่ายเหลือ 0

<h2>design interface(s) to represent at least two types of rpg characters</h2>

เราจะมี `abstract class character` เป็น parent class ของ knight และ archer ที่เราจะสร้าง
* <h2>character.java</h2>

<h3>instance variables</h3>

* `string name` - ชื่อของ rpg character (ไม่ใช่ชนิดของ rpg character)
* `int level` - ระดับ
* `double hp` - health power
* `double attackpower` - พลังในการโจมตี
* `double defensepower` - พลังในการป้องกัน
* `double accessorynummax` - จํานวนของ accessory ที่มากที่สุดที่จะเก็บได้
* `arraylist<accessory> accessorylist` - list ที่เก็บ accessory แต่ละอันที่ตัวละครสวมใส่

โดยการตํานวณ power ที่โจมตีสุดท้ายเป็น ``target.hp -= attackpower - target.defensepower`` โดยจะมีการ round ค่าของ power ด้วย

* <h3>instance methods</h3>

* `void attack(character target)` - ทําการโจมตีศัตรู (ในที่นี้เราจะเรียกว่า target) โดย hp ของ target จะลดตาม attackpower ของตัวละครที่โจมตี และ defensepower ของ target โดยถ้า target ตายก็จะ (hp == 0) attackpower, defensepower ของ target จะเป็น 0
* `void showstatus()` - แสดงค่าต่างๆของตัวละครนั้นๆ ได้แก่ level, hp, attackpower, defensepower


* <h2>knight.java (extends character)</h2>

* <h3>instance variables</h3>
  มีตาม class character (เพราะไม่มีเพิ่ม)
  โดย

    * `hp = 80`
    * `defensepower = 5 + level * 0.5`
    * `attackpower = 10 + level * 0.5`
    * `accessorynummax = 2`


* <h3>instance methods</h3>

    * `void swordmastery()`- ทําการเพิ่มพลังโจมตีของตัวเองตาม lvl ของ skill
    * `void bash(character x)` -ทำการโจมดีโดยพลังโจมตีจะแรงไปตาม lvl ของ skill
    * `void counterattack(character x)` -ปัดดาเมจทั้งหมดที่ไม่ใช่ skill และทำความเสียหายตามดาเมจที่เราปัด

* <h2>archer.java (extends character)</h2>

* <h3>instance variables</h3>

  มีตาม character โดยมีค่าที่เปลี่ยนแปลงดังนี้
    * `hp = 60`
    * `defensepower = 5 + level * 0.5`
    * `attackpower = 15 + level * 0.5`
    * `accessorynummax = 2  + (level/2)`

* <h3>instance methods</h3>

    * `void doubleshot(character x)` - โจมตีโดยจะมี damage เป็น 2 เท่าของ attackpower
    * `void piercingarrow (character x)` - ทำดาเมจเท่ากับพลังโจมตี และเป้าหมายไม่สามารถหลบหรือบล็อคสกิลนี้ได้
    * `void evasion(character x)` - หลบจะทําให้ attackpower ที่รับ เป็น 0 (no damage)


<h2>design interface(s) to represent at least two types of accessories</h2>

จะมี `abstract class accessory` เป็น parent class ของ ring, shield, boots ที่เราจะสร้าง โดยมี

* <h2>accessory.java</h2>
  <h3>instance variables</h3>

* `protected int level` -ระดับ
* `protected int bonusattackpower` -โบนัสพลังโจมดี
* `protected int bonusdefencepower` -โบนัสพลังป้องกัน

* <h3>instance methods</h3>

* `void levelup()` - เพิ่ม level ที่ละ 1 ระดับ
* `void levelup(int level)` พิ่ม level ที่ละ level(input ของ method) ระดับ


* <h2>ring.java (extends from accessory)</h2>

* <h3>instance variables</h3>

    * มีตาม class character (เพราะไม่มีเพิ่ม)
      โดยจะมีการคํานวณ `bonusattackpower` ตามสูตรดังนี้ `bonusattackpower = 10 + level * 2`



* <h2>amulet.java (extends from accessory)</h2>

* <h3>instance variables</h3>
* มีตาม class character (เพราะไม่มีเพิ่ม)
  โดยจะมีการคํานวณ `bonusdefensepower` ตามสูตรดังนี้ `bonusdefensepower = 10 + level * 2`


