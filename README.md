# Lab4 - Object Oriented Programming

minimalist RPG game ที่สามารถ run และเล่นใน console ได้เลย รูปแบบเกมจะเล่นสองคนโดยมีclass knight และ archer ที่มีสกิลแตกต่างกันให้เลือกในตอนเริ่มเกม ในแต่ละ turn เราจะสามารถโจมดีและใช้สกิลอย่างละครั้ง ฝ่ายชนะจะเป็นฝ่ายที่ทำให้ hp ของอีกฝ่ายเหลือ 0

<h2>Design interface(s) to represent at least two types of RPG characters</h2>

เราจะมี `abstract class Character` เป็น parent class ของ Knight และ Archer ที่เราจะสร้าง
* <h2>Character.java</h2>

<h3>Instance Variables</h3>

* `String name` - ชื่อของ RPG character (ไม่ใช่ชนิดของ RPG character)
* `int level` - ระดับ
* `double hp` - Health Power
* `double attackPower` - พลังในการโจมตี
* `double defensePower` - พลังในการป้องกัน
* `double accessoryNumMax` - จํานวนของ Accessory ที่มากที่สุดที่จะเก็บได้
* `ArrayList<Accessory> accessoryList` - list ที่เก็บ Accessory แต่ละอันที่ตัวละครสวมใส่

โดยการตํานวณ power ที่โจมตีสุดท้ายเป็น ``target.hp -= attackPower - target.defensePower`` โดยจะมีการ Round ค่าของ power ด้วย

* <h3>Instance Methods</h3>

* `void attack(Character target)` - ทําการโจมตีศัตรู (ในที่นี้เราจะเรียกว่า target) โดย hp ของ target จะลดตาม attackPower ของตัวละครที่โจมตี และ defensePower ของ target โดยถ้า target ตายก็จะ (hp == 0) attackPower, defensePower ของ target จะเป็น 0
* `void showStatus()` - แสดงค่าต่างๆของตัวละครนั้นๆ ได้แก่ level, hp, attackPower, defensePower


* <h2>Knight.java (extends Character)</h2>

* <h3>Instance Variables</h3>
  มีตาม class Character (เพราะไม่มีเพิ่ม)
  โดย

  * `hp = 80`
  * `defensePower = 5 + level * 0.5`
  * `attackPower = 10 + level * 0.5`
  * `accessoryNumMax = 2`


* <h3>Instance Methods</h3>

  * `void SwordMastery()`- ทําการเพิ่มพลังโจมตีของตัวเองตาม lvl ของ skill
  * `void Bash(Character x)` -ทำการโจมดีโดยพลังโจมตีจะแรงไปตาม lvl ของ skill
  * `void CounterAttack(Character x)` -ปัดดาเมจทั้งหมดที่ไม่ใช่ skill และทำความเสียหายตามดาเมจที่เราปัด

* <h2>Archer.java (extends Character)</h2>

* <h3>Instance Variables</h3>

  มีตาม Character โดยมีค่าที่เปลี่ยนแปลงดังนี้
  * `hp = 60`
  * `defensePower = 5 + level * 0.5`
  * `attackPower = 15 + level * 0.5`
  * `accessoryNumMax = 2  + (level/2)`

* <h3>Instance Methods</h3>

  * `void DoubleShot(Character x)` - โจมตีโดยจะมี damage เป็น 2 เท่าของ attackPower
  * `void PiercingArrow (Character x)` - ทำดาเมจเท่ากับพลังโจมตี และเป้าหมายไม่สามารถหลบหรือบล็อคสกิลนี้ได้
  * `void Evasion(Character x)` - หลบจะทําให้ attackPower ที่รับ เป็น 0 (no damage)


<h2>Design interface(s) to represent at least two types of accessories</h2>

จะมี `abstract class Accessory` เป็น parent class ของ ring, shield, boots ที่เราจะสร้าง โดยมี

* <h2>Accessory.java</h2>
  <h3>Instance Variables</h3>

* `String name` - ชื่อของ Accessory
* `protected int level` -ระดับ
* `protected int bonusAttackPower` -โบนัสพลังโจมดี
* `protected int bonusDefencePower` -โบนัสพลังป้องกัน

* <h3>Instance Methods</h3>

* `void levelUp()` - เพิ่ม level ที่ละ 1 ระดับ
* `void levelUp(int level)` พิ่ม level ที่ละ level(input ของ method) ระดับ


* <h2>Ring.java (extends from Accessory)</h2>

* <h3>Instance Variables</h3>

  * มีตาม class Character (เพราะไม่มีเพิ่ม)
    โดยจะมีการคํานวณ `bonusAttackPower` ตามสูตรดังนี้ `bonusAttackPower = 10 + level * 2`



* <h2>Amulet.java (extends from Accessory)</h2>

* <h3>Instance Variables</h3>
* มีตาม class Character (เพราะไม่มีเพิ่ม)
  โดยจะมีการคํานวณ `bonusDefensePower` ตามสูตรดังนี้ `bonusDefensePower = 10 + level * 2`


