# vana-sixgpt


## Sistem gereksinimleri güncelleyerek başlıyoruz
```
curl -sSL https://raw.githubusercontent.com/Hitasyurekk/vana-sixgpt/main/update.sh | bash
```
## Sixgpt giriş

*Önce dosya oluşturmamız gerekiyor*
```
mkdir sixgpt
cd sixgpt
```

*Daha sonra cüzdan bilgilerimizi girmek için* 
```
export VANA_PRIVATE_KEY=cüzdananahtarınızı
export VANA_NETWORK=satori

export VANA_NETWORK=moksha
```
*Dockes dosyası oluşturma*
```
nano docker-compose.yml
```
*Oluşturduğumuz dosyanın içine bu kodu giriyoruz*

```
version: '3.8'

services:
  ollama:
    image: ollama/ollama:0.3.12
    ports:
      - "11435:11434"
    volumes:
      - ollama:/root/.ollama
    restart: unless-stopped
 
  sixgpt3:
    image: sixgpt/miner:latest
    ports:
      - "3015:3000"
    depends_on:
      - ollama
    environment:
      - VANA_PRIVATE_KEY=${VANA_PRIVATE_KEY}
      - VANA_NETWORK=${VANA_NETWORK}
    restart: always

volumes:
  ollama:
```







  
