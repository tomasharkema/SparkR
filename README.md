# SparkR

Dit document is gemaakt door Tomas Harkema in opdracht van Peter Odenhoven. 
Voor vragen, mail naar: tomas@harkema.io

## Setup

- Installeer VirtualBox
- Download VM van `https://www.dropbox.com/s/th9a3mn2o485ac5/Spark.ova?dl=1`
- Importeer `Spark.ova` in VirtualBox
    - Kies "Reset Mac adresses"
- Check in de netwerk instellingen of de portforwarding goed staat. Poort `2222 -> 22`, `8787 -> 8787`, `4040 -> 4040` en `9995 -> 9995` zouden open moeten staan.
- Start Spark VM


## Testen

- Probeer remote in te loggen op de VM. User is `spark`, password is `spark`. `ssh spark@localhost -p 2222`
- Start Spark en Zepplin door `sudo sh start.sh` te runnen. 
- Check of Zeppelin draait door `http://localhost:9995/` te openen in een browser.
- Check of SparkR draait door een `R` repl te starten en de volgende commands te runnen:

```R
library(SparkR, lib.loc = c(file.path(Sys.getenv("SPARK_HOME"), "R", "lib")))
library(SparkR)
sc <- sparkR.session(master = "local[*]", sparkConfig = list(spark.driver.memory = "2g"))
sqlContext <- sparkRSQL.init(sc)
df <- createDataFrame(sqlContext, iris)
head(df)
```

## Opdracht

- Ga naar de zeppelin interface (`http://localhost:9995/`). 
- Doe de SparkR tutorial via Zepplin Tutorial -> R (SparkR)

## Referenties:
- Tutorial SparkR: https://rpubs.com/wendyu/sparkr
- Spark installation guide: http://blog.prabeeshk.com/blog/2014/10/31/install-apache-spark-on-ubuntu-14-dot-04/
