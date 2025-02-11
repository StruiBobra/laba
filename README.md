# Волобуев Руслан К-ИСП-39-2

Ввел команду   **sudo yum install wget**  она устанавливает утилиту wget в системах



![image](https://github.com/user-attachments/assets/1eb5d27a-1c93-4711-9991-fcc7c7577c9f)


Вылезла ошибка, вводим команду   **su root**   далее   **vi /etc/sudoers**    и делаю изменения в файле, выхожу и сохраняю shift+Ж, :wq!

![image](https://github.com/user-attachments/assets/f1168eaa-198f-4e55-be4c-d6316fb5c107)


Установил wget

![image](https://github.com/user-attachments/assets/93e57ee6-43e6-4bb7-876c-3d6894058422)


Ввел команду     **sudo yum install**     curl для установки утилиты curl

![image](https://github.com/user-attachments/assets/26b3e8b4-bed3-4c81-b7d2-45b548f9c83a)



Ввожу команду sudo   **wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo** она скачивает конфигурационный файл для репозитория Docker


![image](https://github.com/user-attachments/assets/d6a64bdf-168b-4849-a87b-64f44dfb4b6e)

Устанавливаю докер   **sudo yum install docker-ce docker-ce-cli containerd.io**   (устанавливает Docker и необходимые для его работы пакеты)


![image](https://github.com/user-attachments/assets/f8715b95-7868-4a26-b4f6-c809d1c13c87)

Cоглашаюсь, чтобы завершить процесс установки 

Ввожу команду  **sudo systemctl enable docker --now** что бы запустить *Doker*
Эта команда настраивает автозапуск Docker при старте системы

![{3D61C90A-AD6C-477E-ABA6-9BE9E5AB3DE3}](https://github.com/user-attachments/assets/20d716f9-02de-4721-82d4-7b71672beb27)

