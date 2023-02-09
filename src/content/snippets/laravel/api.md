---
title: Laravel Api
slug: api-Laravel
excerpt: Api with Laravel 9
author: ali
image: 'https://cdn.static-economist.com/sites/default/files/images/2015/09/blogs/economist-explains/code2.png'
---

create album api

### all Tasks

1. [x] Install Laravel
2. [x] Database Models
3. [x] Album Curd
4. [x] Laravel Resources
5. [x] Versioning
6. [x] Image Resize
7. [x] Image Api Endpoint
8. [x] Login & Registration
9. [x] Authentication In Api
10. [x] Deploy To Host

## Database schema

### image manipulation table

- id Int
- name Varchar(255)
- path Varchar(2000)
- type Varchar(25)
- data text
- output_path varchar(2000)
- created_at TIMESTAMP
- user_id Int
- album_id Int

### Album table

- id Int
- name Varchar(255)
- created_at TIMESTAMP
- updated_at TIMESTAMP
- user_id Int

### user table

- id Int
- name Varchar(255)
- email Varchar(255)
- password Varchar(255)
- created_at TIMESTAMP
- updated_at TIMESTAMP

## create album migration

```php
 public function up(){
    Schema::create('albums',function(Blueprint $table)){
        $table->id();
        $table->string('name',255);
        $table->timestamps();
        $table->foreignIdFor(\App\Models\User::class,'user_id');
    }
 }

```

## create Image_manipulations migration

```php
 public function up(){
    Schema::create('image_manipulations',function(Blueprint $table)){
        $table->id();
        $table->string('name',255);
        $table->string('path',2000);
        $table->string('type',25);
        $table->text('data');
        $table->string('output_path',2000);
        $table->timestamps();
        $table->foreignIdFor(\App\Models\User::class,'user_id');
        $table->foreignIdFor(\App\Models\Album::class,'album_id');
    }
 }

```

### create Album Controller

```cli
php artisan make:controller AlbumController --model=Album --requests --api
```

### make rules in StoreAlbumRequest

```php
public function rules() {
    return [
        'name'=>'required'
    ]
}

```

### create new Album action

```php
public function store(StoreAlbumRequest $request){
   $album= Album::create($request->all());
   return $album;

//    or use resource
return new AlbumResource($album);
}
```

## setup the route

```php
// this route well use all endpoint resource
Route::apiResource('album',\App\Http\Controller::class);

```

## Get all the albums

```php
public function index(){
    return Album::all();
}

```

### Get single album

```php
public function show(Album $album){
    return $album;


 //    or use resource
  return new AlbumResource($album);
}

```

### Update the album

```php
public function update(Album $album, Request $request){
    $album->update($request->all());

    return $album;


  //    or use resource
   return new AlbumResource($album);
}

```

### Delete Album

```php
public function delete(Album $album){
   $album->delete();

   return response('',204);
}

```

# setup Versioning

### first setup the route prefix and grouping

```php
Route::prefix('v1')->group(function(){
    Route::apiResource('album',\App\Http\AlbumController::class);
})

```

# Api Resources

when building an api,you may need a transformation layer that sits between your Eloquent models and the Json responses that are actually returned to your application's users, For example you may wish to display certain attributes for a subset of users and not others , or you may wish to always include certain relationships in the Json representation of your models, Eloquent's Resource classes allow you to expressively and easily transform your models and model collection into Json

## generating album resource

```cli
php artisan make:resource V1\\AlbumResource

```

## get all albums with resource

```php
public function index(){
    return AlbumResource::collection(Album::all());

    // or use pagination
    return AlbumResource::collection(Album::paginate());


}

// in  album resource
public function toArray(){
    return [
        'id'=>$this->id,
        'name'=>$this->name,
        'created_at'=>$this->created_at,
        'updated_at'=>$this->updated_at,
    ]
}

```

### create image_manipulations [controller,resource]

**create controller**

```php
php artisan make:controller V1\\ImageManipulationController --model=ImageManipulation --requests --api

```

**create image manipulator resource**

```php
php artisan make:resource  V1\ImageManipulation

```
