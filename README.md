Untitled
================

导入移民和GDP数据
-----------------

``` r
gdp <- read.csv(url("https://raw.githubusercontent.com/danalysis/migrate-GDP/master/data/API_NY.GDP.PCAP.CD_DS2_zh_csv_v2.csv"), header=TRUE, stringsAsFactors = FALSE)
mig <- read.csv(url("https://raw.githubusercontent.com/danalysis/migrate-GDP/master/data/Data.on.the.global.flow.of.people_Version.March2014.csv"), header=TRUE, stringsAsFactors = FALSE)
met <- read.csv(url("https://raw.githubusercontent.com/danalysis/migrate-GDP/master/data/Metadata_Country_API_NY.GDP.PCAP.CD_DS2_zh_csv_v2.csv"), header=TRUE, stringsAsFactors = FALSE)
```

对GDP数据进行清洗
-----------------

    ##   Country.Code         Income.Group
    ##  ABW    :  1   低收入国家    :31   
    ##  AFG    :  1   中低等收入国家:51   
    ##  AGO    :  1   中高等收入国家:53   
    ##  ALB    :  1   高收入国家    :79   
    ##  AND    :  1   NA's          :34   
    ##  ARB    :  1                       
    ##  (Other):242

    ##   Country.Code   Income.Group
    ## 1          ABW     高收入国家
    ## 2          AFG     低收入国家
    ## 3          AGO 中高等收入国家
    ## 4          ALB 中高等收入国家
    ## 5          AND     高收入国家
    ## 6          ARB           <NA>

合并移民和GDP数据（2000-2005）
------------------------------

    ##       mig.country_dest_id mig.country_orig_id mig.country_orig
    ## 36249                 USA                 MEX           Mexico
    ## 806                   ARE                 IND            India
    ## 36132                 USA                 IND            India
    ## 849                   ARE                 BGD       Bangladesh
    ## 16045                 IND                 BGD       Bangladesh
    ## 36213                 USA                 CHN            China
    ##           mig.country_dest mig.countryflow_2005 mig.orig.income.group
    ## 36249        United States              1957397        中高等收入国家
    ## 806   United Arab Emirates              1149965        中低等收入国家
    ## 36132        United States               701242        中低等收入国家
    ## 849   United Arab Emirates               646729        中低等收入国家
    ## 16045                India               630451        中低等收入国家
    ## 36213        United States               615536        中高等收入国家
    ##       mig.dest.income.group
    ## 36249            高收入国家
    ## 806              高收入国家
    ## 36132            高收入国家
    ## 849              高收入国家
    ## 16045        中低等收入国家
    ## 36213            高收入国家

结论
----

在2000~2005年间，在全球所有移民人口中，93%的人口从GDP水平较低的国家，移民到GDP水平较高的国家

    ##   Direction   Number        Pct
    ## 1      L->H 38565075 0.93156381
    ## 2      H->L  2833136 0.06843619

71%的移民人口来自于中等收入国家，是移民的主力军

    ##          Group.1        x       pct
    ## 2 中低等收入国家 19427348 0.4685342
    ## 3 中高等收入国家 10302000 0.2484559
    ## 4     高收入国家  7227449 0.1743062
    ## 1     低收入国家  4507304 0.1087038

高收入国家接受来自全球75%的移民人口

    ##          Group.1        x        pct
    ## 4     高收入国家 31042497 0.74952133
    ## 3 中高等收入国家  5437351 0.13128488
    ## 1     低收入国家  2492353 0.06017788
    ## 2 中低等收入国家  2444228 0.05901590
