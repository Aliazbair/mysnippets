---
title: Laravel Query
slug: Laravel
excerpt: laravel Query
author: ali
image: 'https://cdn.static-economist.com/sites/default/files/images/2015/09/blogs/economist-explains/code2.png'
---



```php

public function filter(){

    // create query instances
    $query=Model::query();

    // make search filter
    if($s= $request->input('s')){
        // make query
        $query->whereRaw("title LIKE %'". $s. "%'")
        ->orWhereRow("name LIKE '%" . $s. "%'");

    }

    // sort filter
    if($sort =$request->input('sort')){
        $query->orderBy('price'.$sort);
    }

    // make pagination
    $parPage=9;
    $page=$request->input('page',1);
    $total=$query->count();

    // make results
    $result=$query->offset(($page - 1) * $parPage)->limit($parPage)->get();

    return [
        'data'=>$result,
        'total'=> $total,
        'page'=>$page,
        'last_page'=>ceil($total / $parPage)

        ]
}


```
