# Retrofit使用

## How to use

- Relesse下载app-debug.apk

- 对应目录下终端运行

  **adb install -t app-debug.apk**

  

## TODO-1 做网络请求

```java
apiService.register(name, password, repassword).enqueue(new Callback<com.byted.chapter5.UserResponse>() {
                    @Override
                    public void onResponse(Call<com.byted.chapter5.UserResponse> call, Response<com.byted.chapter5.UserResponse> response) {
                        if(response.body() != null && response.body().user != null){
                            Toast.makeText(RegisterActivity.this,"注册成功" + response.body().user.nickname,
                                    Toast.LENGTH_SHORT).show();
                        }
                        else if(response.body() != null){
                            Toast.makeText(RegisterActivity.this,"注册失败" + response.body().errorMsg,
                                    Toast.LENGTH_SHORT).show();
                        }
                    }

                    @Override
                    public void onFailure(Call<com.byted.chapter5.UserResponse> call, Throwable t) {
                        Toast.makeText(RegisterActivity.this, "网络失败" + t.getMessage(),
                                Toast.LENGTH_SHORT).show();
                    }
                });
```



## TODO-2 添加api

```java
@FormUrlEncoded
    @POST("user/register")
    Call<UserResponse> register(@Field("username") String userName, @Field("password") String password, @Field("repassword") String repassword);

```

 

