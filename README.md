# GitLab runner

Подрезал скрипты с бесплатной части курса Slurm (https://edu.slurm.io/). 
Представлено для учебных целей, чтобы показать как создаётся и запускается runner.

## Как работает

Я проверял на Ubuntu 22.04.2 LTS

```
git clone https://github.com/GithubcomRoman/devops_gitlab_runner.git
cd devops_gitlab_runner
```

Перед тем как начать регистрировать раннер, надо сходит в GitLab, выбрал нужный проект (создать тестовый). Далее слева выбрать Settings->CI/CD->Runners. Там будет написано "And this registration token:". Этот токен нужне будет в ответах на вопросы ниже.

Запуск регистрации раннера:

```bash
bash register.sh
```

```
Ответы на вопросы:
Please enter the gitlab-ci coordinator URL (e.g. https://gitlab.com/):
http://10.10.10.241/
Please enter the gitlab-ci description for this runner:
[5a2f4275a151]: runner1
Please enter the gitlab-ci tags for this runner (comma separated):
runner1,test,docker
Registering runner... succeeded                     runner=GR134894
Please enter the executor: parallels, shell, ssh, kubernetes, custom, docker, docker-ssh, virtualbox, docker+machine, docker-ssh+machine:
docker
Please enter the default Docker image (e.g. ruby:2.6):
bash:4.4
Runner registered successfully. Feel free to start it, but if it's running already the config should be automatically reloaded!
```

Будет создан файл config/config.toml. Если при вводе данных выше что-то было введено не очень корректно, то можно поправить в этом конфиге, прежде чем ехать дальше.

Запуск раннера:

```bash
bash run.sh
```

Должен появится раннер в Settings->CI/CD->Runners "Available specific runners" с зелёным статусом "Runner is online". Если всё так, то поздравляю! Раннер готов к бою. Осталось написать пайплайн. 
