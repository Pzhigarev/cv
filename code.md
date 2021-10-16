# Code example
_______________

# PHP:

`````
<?php 

	use PDO;

	class DB
	{
		
		private $db;

		
		public function __construct()
		{
			$dbinfo = require 'path/to/dbinfo.php';
			$this->db = new PDO('mysql:host=' . $dbinfo['host'] . ';dbname=' . $dbinfo['dbname'], $dbinfo['login'], $dbinfo['password']);
		}

		
		public function query($sql, $params = [])
		{
			
			$stmt = $this->db->prepare($sql);
			
			
			if ( !empty($params) ) {
				foreach ($params as $key => $value) {
					$stmt->bindValue(":$key", $value);
				}
			}
			
			
			$stmt->execute();
			
			return $stmt->fetchAll(PDO::FETCH_ASSOC);
		}

		public function getAll($table, $sql = '', $params = [])
		{
			return $this->query("SELECT * FROM $table" . $sql, $params);
		}

		public function getRow($table, $sql = '', $params = [])
		{
			$result = $this->query("SELECT * FROM $table" . $sql, $params);
			return $result[0]; 
		}

	}

?>
``````
_______________


# Apex:

``````
public class CampingListController {
    @auraenabled
    public static List<Camping_Item__c> getItems (){
        List<Camping_Item__c> CI = [select id, name,price__c,Quantity__c,Packed__c from Camping_Item__c ];
        return CI;
    }
    @auraenabled
    public static Camping_Item__c saveItem (Camping_Item__c item){
        insert item;
        return item;
    }
}
`````


_______________




# JavaScript:

`````
// user blok
let userName = 'Pavel';
let password = '12345';
let newUser;
let newPassword;
let chek1 = 1;
        
document.querySelector("#a-button").onclick = function(){
// for userName
do{
newUser = prompt('введите логин :','Введите логин');
if (newUser == null) clouse;
} while (newUser !== userName);
// for Password
do{
newPassword = prompt('Введите пароль','Введите пароль');
if (newPassword == null) clouse;
else if (newPassword == password)
chek1 = alert('Добрый день');
}while(newPassword !== password);
}

``````

_______________



# Swift:

````
var array: [Int] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]
 
var newArray = array.filter({$0 % 3==0})
print(newArray) 

````

____________



