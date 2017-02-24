# Quiz3
1.	請解釋 database.yml, routes.rb, 和 Gemifle 分別是什麼？ 他們分別在一個 Rails 專案裡的什麼位置？ 他們為什麼對一個 Rails 專案如此重要？
config/database.yml 這個檔案，包括伺服器位置管理帳號以及密碼重要的資訊。
config/routes.rb 設定URL路徑:root’orders#index’
config/Gemifle 很重要:檢查這個專案理需要的安裝版本及相關程式舉例SQL 資料庫程式 還有Sass-rails ,pry
2.	MVC 架構裡的 M, V, 和 C 分別代表什麼？

模型（Model）的職責
保存應用程式狀態
執行應用程式商務邏輯（Business logic）
畫面（View）的職責
提取模型狀態
執行呈現邏輯（Presentation logic）組織回應畫面
控制器（Controller）的職責
o	接受請求
o	驗證請求
o	判斷要轉發請求給哪個模型
o	判斷要轉發請求給哪個畫面

3.	請解釋 CRUD 是哪四個字的縮寫？
Create,  Read, Update and Delete

4.	請問在 routes.rb 裡面加入以下程式碼會產生出哪一些 url？ (提示：在 browser 輸入http://localhost:3000/rails/info/routes)
resources :users

5.	請解釋 model 檔案和 migration 檔案的差別？

Model :主要設定關聯屬性
Migration: 設定表單內的物件屬性
      t.text :content
      t.integer :commentable_id
      t.string :commentable_type

6.	若今天發現一個 migration 檔寫錯，請問我應該用什麼指令回復到上一個版本的 migration? :
rake db:rollback
7.	假設今天
	我要在資料庫裡產出一個叫 group 的資料表
	裡面包括的欄位名稱和相對應的資料型別是： name (string), description (text), members (integer)
	請寫出一個能產生出以上需求的 migration 檔

class Group < ActiveRecord::Migration[5.0]
	  def change
	    create_table :group do |t|
          t.string :namn
	      t.integer :members
	    
	      t.text :description
	
	      t.timestamps
	    end
	  end
	end
8.	請解釋什麼是 ActiveRecord?

ActiveRecord是SQL語言與Ruby語言的翻譯官，有非常多程式設計其實都是在建立抽象機制，
C 語言簡化了組合組言的繁雜、動態語言如 Ruby 簡化了 C 語言、TCP 協定簡化了 IP 通訊協定，甚至車子的擋風玻璃跟雨刷也簡化了下雨的事實。

9.	若今天需要為 Project 和 Issue 這兩個 Model 建立一對多的關係，請寫出實作上所需要的 migratiion 和 model 檔案
  class Project < ApplicationRecord
    has_many :issues
  end
 class Issue < ApplicationRecord
    belongs_to :projects
  end
	若今天我有以下 model 檔：
class User < ActiveRecord::Base
  has_many :groups_users
  has_many :groups, through: :groups_users 
end
10.	請寫出和這個 model 檔相關連的 model 檔，以及這些 model 檔所需要的資料庫欄位 
class Group < ActiveRecord::Base
  has_many :groups_users
  has_many :users, through: :groups_users 
  validates :group_name, presence: true
end

class Group_user < ActiveRecord::Base
  belongs_to :user
  belongs_to :group
  validates :user_id, presence: true
  validates :group_id, presence: true
end
11.	延續第10題，如果需要讓一個叫 "Bob" 的使用者產生一個名字叫做 "Rails is Fun" 的社團，應該如何在 rails console 裡實作出來？

 User.create(name: "Bob")
 Group.creat(group_name: "Rails is Fun")
 Group_user.create(user_id: "1", group_id: "1")
12.	延續第11題，請寫一段程式碼確保使用者在建立新社團時社團名不可以是空白，而且不能超過50個字

class Group < ActiveRecord::Base
  validates :group_name, presence: true
  validates :group_name, length: { maximum: 100 }
end

