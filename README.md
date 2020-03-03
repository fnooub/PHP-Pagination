# PHP Pagination
===

example.php
``` php
<style>
	ul {list-style: none;}
	li {display: inline; padding: 10px;}
</style>
<?php

include 'Pagination.php';

$cars  = array(
	"Volvo",
	"BMW",
	"Toyota"
);
$total = count($cars);
$limit = 1;

// thiết lập
$config = array(
	'current_page' => isset($_GET['page']) ? $_GET['page'] : 1, // Trang hiện tại
	'total_record' => $total, // Tổng số record
	'limit' => $limit, // limit
	'link_full' => 'example.php?page={page}', // Link full có dạng như sau: domain/com/page/{page}
	'link_first' => 'example.php', // Link trang đầu tiên
	'range' => 6 // Số button trang bạn muốn hiển thị 
);
$paging = new Pagination();
$paging->init($config);

// array data
$data = $paging->show_array($cars);
foreach ($data as $key => $value) {
	echo "<p>$key => $value</p>";
}

// sql data
// SELECT * FROM table LIMIT $paging->get_start, $limit

echo $paging->html();
```
