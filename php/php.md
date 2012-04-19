PHP хэлний код бичих зөвлөмж
----------------------------
Эх сурвалж: [PEAR naming convention](http://pear.php.net/manual/en/standards.naming.php)

	* Догол мөр болон мөрийн урт
	* Control structure
	* Функц дуудах
	* Классын нэршил
	* Функцын нэршил
	* Массив
	* Тайлбар хийх
	* including code
	* PHP кодын tag
	* Файлын эхлэл хэсгийн тайлбар
	* SVN ашиглах
	* Жишээ URL
	* Нэршил
	* Файлын формат
	* E_STRICT горим дахь код
	* Алдаа боловсруулах зөвлөмж
	* Зөв аргачилалууд
	* Dockblock тайлбар агуулсан жишээ файл
	* PEAR багаж
##Догол мөр болон мөрийн урт

Use an indent of 4 spaces, with no tabs. This helps to avoid problems with diffs, patches, SVN history and annotations.

For Emacs you should set indent-tabs-mode to nil. Here is an example mode hook that will set up Emacs (ensure that it is called when you are editing PHP files):

(defun pear/php-mode-init()
  "Set some buffer-local variables."
  (setq case-fold-search t)
  (c-set-offset 'arglist-intro '+)
  (c-set-offset 'arglist-close '0)
)
(add-hook 'php-mode-hook 'pear/php-mode-init)
Here are Vim rules for the same thing:

set expandtab
set shiftwidth=4
set softtabstop=4
set tabstop=4
It is recommended to keep lines at approximately 75-85 characters long for better code readability. Paul M. Jones has some thoughts about that limit.

##Глобал хувьсагч болон функцууд

Хэрэв глобал хувьсагч зарлах шаардлагатай бол хувьсагчийн нэр нь доогуур зураасаар эхэлж package нэр болон хувьсагчийн нэр нь доогуур зураасаар холбогдоно. Жишээ нь PEAR package дотор глобал хувьсагч зарласан гэвэл дараах байдалтай байна.

	```PHP
	$_PEAR_destructor_object_list
	```
Харин глобал функцуудын хувьд package хоорондын давхцалаас сэргийлэх зорилгоор package нэрээр эхэлж "camelCase" байдлаар нэрлэнэ. Жишээ нь:

	```PHP
	XML_RPC_serializeData()
	```
## Классын нэр

Классын нэр нь тодорхой нэрээр нэрлэгдэж аль болох товчилсон нэршил хэрэглэхгүй байх хэрэгтэй. Классын нэр нь үргэлж том үсгээр эхэлнэ. PEAR классын удамшил нь нэртэйгээ шууд холбоотой байх ба доогуур зураасаар тусгаарлагдана. Зөв нэрлэгдсэн классын жишээ:

	```PHP
	Log	
	Net_Finger	
	HTML_Upload_Error
	```
##Классын хувьсагч болон функцууд

Классын хувьсагч болон функцууд нь "camelCase" байдлаар нэрлэгдэнэ. Зарим жишээг дурьдвал:

	```PHP
	$counter
	connect()
	getData()
	buildSomeWidget()
	```

Private class members are preceded by a single underscore. For example:

	```PHP
	$_status	_sort()	_initTree()
	```
	
	Дараах хэсэг нь PHP5-д хамаарна.
Хаалттай классын гишүүн нь доогуур зураасаар эхлэхгүй. Жишээ нь:

	```PHP
	protected $somevar	protected function initTree()
	```

##Тогтмолууд

Тогтмол хувьсагчийн бүх үсэгийг томоор бичих ба доогуур зураасаар үгийг тусгаарлана. Хэрэв ямар нэгэн package-д хамааралтай бол package нэрийг урьд нь том үсгээр бичнэ. Зарим жишээ:

	```PHP
	DB_DATASOURCENAME	SERVICES_AMAZON_S3_LICENSEKEY
	```

	The true, false and null constants are excepted from the all-uppercase rule, and must always be lowercase.
##File Formats

PEAR бичиглэлээр бичиж байгаа бүх файл нь дараах шаардлагыг хангах хэрэгтэй
	*ISO-8859-1 болон UTF-8 кодчилолыг ашиглах
	*ASCII текст байдлаар хадгалах
	*Unix форматтай
		- Мөрийн төгсгөл нь a line feed буюу (LF) байна. LF нь аравтын тооллын 10, наймтын тооллын 012 ба hex 0A. Бусад Macintosh систем дээрх мөрийн төгсгөл (CR) болон Windows систем дээрх (CRLF) ашиглаж болохгүй.
		- PHP кодын төгсгөлд (?>) зөвхөн нэг мөрийн төгсгөл байх хэрэгтэй. Өөрөөр хэлбэл кодын төгсгөлд курсорыг байрлуулахад PHP кодын төгсгөлийн доод мөрөнд байрлаж байна.

Кодчилолыг файлын эхэнд declare(encoding = 'utf-8') байдлаар зарлаж болох юм.
