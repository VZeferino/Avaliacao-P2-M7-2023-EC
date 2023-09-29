# RDS

A primeira coisa que eu fiz foi criar o RDS, usando o PostgreSQL, nivel gratuito e depois definir o acesso para publico.

Após o banco ser criado eu preciso pegar o endpoint e mudar no meu arquivo main.py. Além de que no RDS, em regras e grupo de segurança, definindo para todos os TCPs.

# Backend

Agora eu vou no EC2 criar uma instancia para meu backend. Permiti os tráfegos e criei. Depois da instância ser criada eu aloquei um ip elástico nela. Depois disso eu me conectei na instancia e rodei esses comandos:

```
sudo apt update
sudo apt upgrade
sudo apt install python3 python3-pip -y
```

Depois disso eu clonei o repositório com:

```
git clone https://github.com/VZeferino/Avaliacao-P2-M7-2023-EC.git
```

Depois disso eu me movi até a pasta do backend e baixei os requirements:

```
python3 -m pip install -r requirements.txt
```

para depois rodar meu arquivo main.py:

```
python3 -m main.py
```

É preciso mudar a porta no back com o ipttables

```
sudo iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8000
sudo iptables -I INPUT -p tcp --dport 8000 -j ACCEPT
```

# Frontend

Agora eu vou no EC2 criar uma instancia para meu backend. Permiti os tráfegos e criei. Depois da instância ser criada eu aloquei um ip elástico nela. Depois disso eu me conectei na instancia e rodei esses comandos:

```
sudo apt update
sudo apt upgrade
sudo apt install apache2
```

Depois disso eu clonei o repositório com:

```
git clone https://github.com/VZeferino/Avaliacao-P2-M7-2023-EC.git
```

E copiei meus arquivos do front para a pasta padrão do apache. Para isso eu tive que navegar até a pasta do frontend e então copiar os arquivos:

```
sudo cp index.html script.js styles.css /var/www/html
```

No script.js eu coloquei o ip publico do backend e então a conexão foi feita.
