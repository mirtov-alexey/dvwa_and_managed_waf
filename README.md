# _Установка уязвимого веб приложения (dvwa) в Яндекс Облаке (с помощью terraform) для тестирования managed WAF_

Terraform playbook создаст:
- новую vpc network и vpc subnet;
- внешний vpc address;
- security group для доступа к приложению;
- VM на базе [Yandex Container Solution](https://cloud.yandex.ru/docs/cos/) c запущенным docker контейнером с [Damn Vulnerable Web Application (DVWA)](https://dvwa.co.uk/)

## Пререквизиты
- bash
- [terraform](https://www.terraform.io/downloads.html)
- [cli yandex cloud](https://cloud.yandex.ru/docs/cli/operations/install-cli), пользователь (роль: admin или editor на уровне folder)
## Установка
- скопировать файлы репозитория с помощью git:
```
git clone https://github.com/mirtov-alexey/dvwa_and_managed_waf.git 
```
- заполнить переменные в файле - "variables.tf" (в поле token необходимо ввести либо oauth token пользователя либо [путь к файлу ключа service account](https://cloud.yandex.ru/docs/cli/operations/authentication/service-account))
- в файле "provider.tf" указать token = var.token (для аутентификациии пользователя) или service_account_key_file = var.token (для аутентификации от service account)
- перейти в папку с файлами и запустить terraform init 
```
cd ./dvwa_and_managed_waf/
```
```
terraform init
```
- далее запустить terraform apply
```
terraform apply
```
