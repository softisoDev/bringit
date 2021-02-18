# **Bringit Task Answers**


## **Task-1**

 * How it works?
 * To solve this problem I calculate length and sum of array
 * I use "sum of first n-1 numbers" ===> ((n-1) * n/2)
 * By using this formula I only find missing element, it means it is duplicated number
 
<pre><code> function find_duplicate(array $numbers, $length)
 {
     $sum = 0;
     for ($i = 0; $i<$length; $i++){
         $sum += $numbers[$i];
     }
     return $sum - ((($length - 1) * $length) / 2);
 }</code></pre>
 

## **Task-2**
If we consider that array of size is N then space complexity will be O(N) - **linear complexity**. Because it takes space directly proportional to the input size. Length of each element is 8 bytes then it will be O(N*8). While growing size of array (N) space complexity will increase.
In my opinion instead of using UUID we can use a unique integer.
 

## **Task-3**

##### DB SCHEMA

![](db_schema.png)

I use `WHERE IN` instead of `JOIN`. Because multiple joins show slow performance

3.1 Get last 5 posts  
`select * from posts order by id desc limit 5` (example: result of IDs are 1,2,3,4,5)

3.2 Get comments of posts  
``select * from post_comments where post_comments.post_id in (1,2,3,4,5)``

3.3 Get post with likes of each user
<code><pre>
SELECT 
    users.*, 
    post_likes.post_id, 
    post_likes.user_id 
FROM users 
     INNER JOIN post_likes 
             ON users.id = post_likes.user_id 
WHERE  post_likes.post_id IN ( 1, 2, 3, 4, 5 )
    </pre></code>




