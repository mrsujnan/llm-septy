Download Ollama

```bash
curl -L https://ollama.com/download/ollama-linux-amd64.tgz -o ollama-linux-amd64.tgz
sudo tar -C /usr -xzf ollama-linux-amd64.tgz
```

Start ollama

```bash
ollama serve #in one terminal
ollama -v #in another terminal
```

Run a model

```bash
ollama run <modelname>  #ex:llama3.1 you can seacrh models here https://ollama.com/search
```

Add to startup services

```bash
sudo useradd -r -s /bin/false -U -m -d /usr/share/ollama ollama
sudo usermod -a -G ollama $(whoami)
sudo nvim /etc/systemd/system/ollama.service
```

Add this to ollama.service

```bash
[Unit]
Description=Ollama Service
After=network-online.target

[Service]
ExecStart=/usr/bin/ollama serve
User=ollama
Group=ollama
Restart=always
RestartSec=3
Environment="PATH=$PATH"

[Install]
WantedBy=default.target
```

Start the service and enable it

```bash
sudo systemctl daemon-reload
sudo systemctl enable ollama
sudo systemctl start ollama
sudo systemctl status ollama
```
