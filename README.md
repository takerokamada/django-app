# django_test
勉強用

## 手順
`docker-compose up -d`

`docker container ls`
コンテナの確認

`docker container exec -it {CONTAINER_ID} django-admin startproject {PROJECT_NAME}`
PROJECT_NAMEには半角英数字でプロジェクト名を設定

作成されたプロジェクトディレクトリ内 
`{PROJECT_NAME}/{PROJECT_NAME}/settings.py`の各設定を変更

### DATABASES
```
DATABASES = {
    'default': {
    'ENGINE': 'django.db.backends.postgresql',
    'NAME': 'postgres',
    'USER': 'postgres',
    'HOST': 'db',
    'PORT': 5432,
  }
}
```


### ALLOWED_HOSTS
```
ALLOWED_HOSTS = ['localhost', '192.168.33.15', '[::1]']
```

または特に設定しない場合は
```
ALLOWED_HOSTS = ['*']
```

### Djangoプロジェクト起動
`docker container exec -it {CONTAINER_ID} python {PROJECT_NAME}/manage.py runserver 0.0.0.0:8000`


### アクセス
`ALLOWED_HOSTS`で設定したIPと
PORTは`docker-compose.yml`で設定してあるもの（今回は8000）でアクセス
`http://192.168.33.15:8000`