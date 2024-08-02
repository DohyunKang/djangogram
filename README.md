# Djangogram

이 프로젝트는 강의를 보고 따라한 클론 코딩 프로젝트입니다. 이 프로젝트는 Django를 사용하여 인스타그램과 유사한 소셜 네트워크 서비스를 구현하였습니다.

## 소개

Behold My Awesome Project!

[![Built with Cookiecutter Django](https://img.shields.io/badge/built%20with-Cookiecutter%20Django-ff69b4.svg?logo=cookiecutter)](https://github.com/cookiecutter/cookiecutter-django/)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)

License: MIT

## 설정

설정에 대한 자세한 내용은 [settings](http://cookiecutter-django.readthedocs.io/en/latest/settings.html)에서 확인할 수 있습니다.

## 기본 명령어

### 사용자 설정

- **일반 사용자 계정**을 생성하려면, 회원 가입 페이지로 이동하여 양식을 작성합니다. 제출 후 "이메일 주소 확인" 페이지가 나타납니다. 콘솔에서 시뮬레이션된 이메일 확인 메시지를 확인하고 링크를 복사하여 브라우저에 입력합니다. 위 과정을 통해 사용자의 이메일이 확인되고 준비가 완료됩니다.

- **슈퍼유저 계정**을 생성하려면 다음 명령어를 사용합니다:

      $ python manage.py createsuperuser

편의를 위해 일반 사용자로는 Chrome에 로그인하고, 슈퍼유저로는 Firefox(또는 유사 브라우저)에 로그인하여 두 종류의 사용자가 사이트에서 어떻게 동작하는지 확인할 수 있습니다.

### 타입 체크

mypy를 사용하여 타입 체크를 실행합니다:

    $ mypy djangogram

### 테스트 커버리지

테스트를 실행하고 커버리지를 확인하며 HTML 커버리지 리포트를 생성합니다:

    $ coverage run -m pytest
    $ coverage html
    $ open htmlcov/index.html

#### pytest를 사용하여 테스트 실행

    $ pytest

### 라이브 리로딩 및 Sass CSS 컴파일

라이브 리로딩 및 Sass 컴파일에 대한 내용은 [Live reloading and SASS compilation](https://cookiecutter-django.readthedocs.io/en/latest/developing-locally.html#sass-compilation-live-reloading)에서 확인할 수 있습니다.

## 배포

이 섹션에서는 이 애플리케이션을 배포하는 방법에 대해 설명합니다.

### Heroku에 배포

1. **Heroku CLI 설치**: Heroku CLI를 설치합니다. (설치 방법은 [Heroku 공식 문서](https://devcenter.heroku.com/articles/heroku-cli)를 참조하십시오.)

2. **Heroku 로그인**: Heroku CLI에 로그인합니다.

    ```sh
    heroku login
    ```

3. **Heroku 애플리케이션 생성**: Heroku 애플리케이션을 생성합니다.

    ```sh
    heroku create your-app-name
    ```

4. **애플리케이션 설정**: 필요한 환경 변수를 Heroku에 설정합니다.

    ```sh
    heroku config:set DEBUG=False
    heroku config:set SECRET_KEY='your-secret-key'
    ```

5. **배포 준비**: `Procfile`과 `requirements.txt` 파일이 프로젝트에 있는지 확인합니다.

    ```sh
    echo "web: gunicorn your_project_name.wsgi --log-file -" > Procfile
    pip freeze > requirements.txt
    ```

6. **코드 배포**: Heroku에 코드를 배포합니다.

    ```sh
    git push heroku main
    ```

7. **데이터베이스 마이그레이션**: Heroku에 데이터베이스 마이그레이션을 실행합니다.

    ```sh
    heroku run python manage.py migrate
    ```

8. **애플리케이션 실행**: 애플리케이션이 정상적으로 실행되는지 확인합니다.

    ```sh
    heroku open
    ```

### AWS에 배포

1. **AWS 계정 생성**: AWS 계정을 생성합니다. (이미 계정이 있다면 이 단계를 건너뜁니다.)

2. **Elastic Beanstalk 설정**: AWS Elastic Beanstalk을 사용하여 애플리케이션을 배포합니다. 자세한 내용은 [AWS Elastic Beanstalk 문서](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/create-deploy-python-django.html)를 참조하십시오.

3. **환경 구성**: 필요한 AWS 리소스(S3, RDS 등)를 구성하고 환경 변수를 설정합니다.

4. **코드 배포**: AWS Elastic Beanstalk CLI를 사용하여 코드를 배포합니다.

    ```sh
    eb init -p python-3.8 djangogram
    eb create djangogram-env
    eb deploy
    ```

5. **데이터베이스 마이그레이션**: AWS에서 데이터베이스 마이그레이션을 실행합니다.

    ```sh
    eb ssh
    python manage.py migrate
    ```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

- **Dohyun Kang** - [GitHub](https://github.com/DohyunKang)

## Acknowledgements

- Thanks to everyone who contributed to this project and provided support.
