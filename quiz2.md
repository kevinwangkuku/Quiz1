# quiz2


1. 請用簡單的方式敘述以下每一行程式碼：

  ```ruby 
  a = 1  #宣告變數a，
  @a = 2 ＃宣告一個ㄕ
  @@a = 5
  user = User.new
  user.name
  user.name = "Joe"
  ```
  宣告一個變數a並且指派數值1到變數a
  
  宣告一個實例變數a並且指派數值2到實例變數a
  宣告一個類別變數a並且指派數值5到類別變數a
  建立一個User類別實例並指派給變數user
  取得user物件的實例變數name
  指派"Joe"字串給user物件的實例變數name

2. 什麼是 module? 請寫一段程式碼說明一個 class 要如何使用一個 module 裡面的 method?

module flyadle
  def fly
    puts "I can fly"
  end
end

clss cat
  include flyble 
end

kitty = cat.new

kitty.fly

3. 請說明 class variable 和 instance variable 之間的差別

class variable: @@ver 變數名稱前加上@@，並且在類別的最外層宣告
instance variable @ver 變數名稱前加上@，並且只能宣告在函式裡，通常是宣告在initialize


4. 請說明 class method 和 instance method 之間的差別

class Greeting 
  def hello
    "hi"
  end

  def self.hello
     "hi"
  end
end

class method 在method名稱前加上self.
instance method 一般method的宣告方式




5. 如果今天我為一個叫 User 的 class 產生一個新物件的方式是:
  ```ruby
  User.new("Bob", "male", "Engineer")
  ```
請寫出 User class 的 initialize method

class User
  def initialize(name, sex, job)
    @name = name
    @sex = sex
    @job = job
  end
end


6. 在：A.  一個 class 裡，method 外面  B.  一個 class 裡，instance method 裡
  self 分別是指向什麼?

在定義一個class時，將self放在method外面就等同於是在類別層級的宣告，此時的Self是指向class。在method裡宣告的self是物件層級，指向的是呼叫該method的物件。


7. attr_accessor 的功能是什麼，它和 attr_reader、attr_writer 之間的差別是什麼？

attr_accessor: 宣告後可以直接呼叫實體
attr_reader：宣告後只會幫你產生getter
attr_writer: 宣告後會幫你產生 getter setter


8. 請說明 public 和 private method 之間的不同

pubilc  :主要針對整個class的所有類別
private :主要是class裡面的父“子”使用．

9. 請說明 Inheritance 和 Module 之間的差別，它們分別是用於哪些情況？ 請舉例說明

  Inheritance 屬性關係繼承   ＥＸ：奶茶屬於 茶類
  module      ＥＸ：珍珠＋奶茶 抹茶＋奶茶 耶果＋奶茶 

10. 若今天有一個 class 有 include 一個 module，他的 parent class 和 sub class 是否可以使用該 module 裡的 method?
parent class無法使用module裡的method，sub class則可以使用

11. 請間單說明什麼是 Relational Database，什麼是 SQL

關聯式資料庫是採用關係模型作為數據組織方式，再依此基礎建出系統架構的資料庫。關聯式資料庫的特點在於它將每個具有相同屬性的數據獨立地存儲在一個表中。對任一表而言，用戶可以新增、刪除和修改表中的數據，而不會影響表中的其他數據
SQL，結構化查詢語言（Structural Query Language），是一種特殊目的之程式語言，用於資料庫中的標準資料查詢語言，作為關係式資料庫管理系統的標準語言（ＣＲＵＤ）