# 장고걸스 튜토리얼 따라하기

Python 3.9.0
Django 3.1.4

- 장고걸스 튜토리얼
  - https://tutorial.djangogirls.org/
- 장고걸스 튜토리얼 심화
  - https://tutorial-extensions.djangogirls.org/ko/

- pythonanywhere.com URL
  - http://rock1191.pythonanywhere.com/admin

ID/PW: admin/admin

## pythonanywhere.com 배포
### 1. git clone
```bash
$ git clone https://github.com/<github-사용자-이름>/my-first-blog.git <파이썬애니웨어-사용자-이름>.pythonanywhere.com
```

### 2. mkvirtualenv 생성
```bash
$ mkvirtualenv --python=python3.8 <your-pythonanywhere-username>.pythonanywhere.com
```

### 3. django 설치
```bash
(<파이썬애니웨어-사용자-이름>.pythonanywhere.com) $ pip install django
```

### 4. 데이터베이스 생성하기
```bash
$ python manage.py migrate
```

### 5. 슈퍼유저 생성하기
```bash
$ python manage.py createsuperuser
```

### 6. 정적 파일 모으기
```bash
$ python manage.py collectstatic
```

### 7. Web 설정
1. Web - Add a new web app
2. manual configuration 선택
3. Virtualenv 'Enter the path to a virtualenv' 클릭
4. /home/<파이썬애니웨어-사용자-이름>/.virtualenvs/<파이썬애니웨어-사용자-이름>.pythonanywhere.com 입력

### 8. WSGI 파일 설정
Code 의 WSGI configuration file 에서 
`/var/www/<your-PythonAnywhere-username>_pythonanywhere_com_wsgi.py` 을 클릭해서 아래의 내용으로 수정

```python
import sys

path = '/home/<your-pythonanywhere-username>/<your-pythonanywhere-username>.pythonanywhere.com'
if path not in sys.path:
    sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()
```

### 9. 동작 확인
Reload 후 웹사이트 접속 확인