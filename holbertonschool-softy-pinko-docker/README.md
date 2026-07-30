# holbertonschool-softy-pinko-docker

Bu repo tapşırıqların (task0 - task6) hazır fayllarını ehtiva edir.

## ⚠️ ÖNƏMLİ - Front-end reponu klonlamaq

Bu mühitdə (sandbox) internetə çıxış olmadığı üçün `softy-pinko-front-end`
reposunu sizin əvəzinizə klonlaya bilmədim. task2, task3, task5 və task6
qovluqlarındakı `front-end/` altında bu komandanı özünüz işə salmalısınız:

```bash
cd task2/front-end   # (task3, task5, task6 üçün də eyni qovluqda)
git clone https://github.com/atlas-school/softy-pinko-front-end
```

Bundan sonra:
- task2/front-end/ üçün heç bir dəyişiklik lazım deyil.
- task3/front-end/ üçün `INDEX_HTML_CHANGES.md` faylındakı dəyişiklikləri
  `softy-pinko-front-end/index.html`-ə əlavə edin.
- task4/front-end/ eyni index.html-i (task3-dəki kimi) istifadə edir.
- task5/front-end/ və task6/front-end/ üçün öz `INDEX_HTML_CHANGES.md`
  faylındakı (proxy versiyalı `/api/hello`) dəyişiklikləri əlavə edin.

Klonlamadan sonra hər front-end qovluğunda bu struktur olmalıdır:

```
front-end/
├── Dockerfile
├── softy-pinko-front-end.conf
└── softy-pinko-front-end/   <- klonlanmış repo
    └── index.html (redaktə olunmuş)
```

## Qovluq strukturu

```
task0/               - İlk Docker image (Ubuntu + Hello World)
task1/                - Flask back-end (api.py, Dockerfile)
task2/
  back-end/           - Flask back-end
  front-end/          - Nginx + statik sayt (klon lazımdır)
task3/
  back-end/           - Flask + flask-cors back-end
  front-end/          - Nginx front-end (klon + JS/HTML dəyişiklikləri lazımdır)
task4/
  back-end/, front-end/, docker-compose.yml
task5/
  back-end/, front-end/, proxy/, docker-compose.yml
task6/
  back-end/, front-end/, proxy/, docker-compose.yml, 2-api-servers.txt
```

## Hər task üçün işə salma

**task0:**
```bash
docker build -f ./task0/Dockerfile -t softy-pinko:task0 ./task0
docker run -it --rm --name softy-pinko-task0 softy-pinko:task0
```

**task1:**
```bash
docker build -f ./task1/Dockerfile -t softy-pinko:task1 ./task1
docker run -p 5252:5252 -it --rm --name softy-pinko-task1 softy-pinko:task1
```

**task2:**
```bash
docker build -f ./task2/back-end/Dockerfile -t softy-pinko-back-end:task2 ./task2/back-end
docker build -f ./task2/front-end/Dockerfile -t softy-pinko-front-end:task2 ./task2/front-end
docker run -p 5252:5252 -it --rm --name softy-pinko-back-end-task2 softy-pinko-back-end:task2
docker run -p 9000:9000 -it --rm --name softy-pinko-front-end-task2 softy-pinko-front-end:task2
```

**task3:** eyni qayda ilə back-end və front-end ayrı-ayrı build/run edilir (2 terminal).

**task4, task5, task6:**
```bash
cd task4  # ya da task5 / task6
docker-compose build
docker-compose up
```

task6 üçün 2 (və ya daha çox) back-end serveri üçün:
```bash
docker-compose up --scale back-end=2
```
