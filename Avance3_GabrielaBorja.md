# Trabajo final Gabriela Aridai Borja Martínez.

## BioinfoRepro2018-II

*****

#### *Sistema de trabajo:*

Dado que la coloración es una característica sujeta a selección, que puede conducir a aislamiento reproductivo, la sitemática tradicional ha utilizado variaciones de color como caractéres que permiten la identificación de especies. Buscando **señales de aislamiento y selección** se analizaron **dos especies** del genéro Acanthurus, del complejo de especies de peces cirujano (*Surgeonfish*): <span style="color:red">*Acanthurus olivaceus*</span> y <span style="color:purple">*Acanthurus reversus*</span>. El primero se distribuye en el Pacífico Central y Hawai, mientras que el segundo en Las Marquesas. Para este estudio se incluyeron **nueve islas**.



Los datos **RAD-seq** trabajados para este proyecto fueron obtenidos del repositorio de datos Dryad.

Gaither MR, Bernal MA, Coleman RR, Bowen BW, Jones SA, Simison WB, Rocha LA (2015)  [Genomic signatures of geographic isolation and natural selection in coral reef fishes.](http://doi.org/10.1111/mec.13129) Molecular Ecology 24(7): 1543-1557.

Gaither MR, Bernal MA, Coleman RR, Bowen BW, Jones SA, Simison WB, Rocha LA (2015) [Data from:](http://doi.org/10.5061/dryad.581f3) Genomic signatures of geographic isolation and natural selection in coral reef fishes. Dryad Digital Repository.

Este trabajo tiene como objetivo implementar algunos de los análisis bioinformáticos realizados en el artículo previamente citado. Dichos análisis se realizaron en un software  diferente para poder realizar una comparación con los análisis originales. Los análisis se documentarán de forma adecuada para garantizar su **reproducibilidad.**

El trabajo se encuentra organizado en los siguientes *directorios*:
- `bin` Contiene los scripts con los pipeline utilizados para cada software en las distitas etapas de análisis.
- `Data` Contiene los inputs requeridos y outputs generados por cada  software organizados en sus respectivos directorios
- `Plots` contiene todas las figuras y gráficas generados.

- - -
#### 1.Filtrado de calidad

Pese a que las secuencias descargadas se reportan como filtradas y desmultiplexeadas, se verificó la calidad de las secuencias usando la imagen de **Biocontainers *Fastqc* **. Todas las muestras, tanto de <span style="color:purple">*A. reversus*</span> como de <span style="color:red">*A. olivaceus*</span> presentaron las bases **3 y 4** fuera de los estándares de calidad, por lo que fueron eliminadas utilizando **Biocontainers *fastxtools* **. Posiblemente esto se deba a que los adaptadores no fueron removidos.

- - -
#### 2. Ensamble con genoma de referencia y llamado de SNPs
El ensamblado con **genoma de referencia** y llamado de SNPs se realizó con el  [software](http://http://ipyrad.readthedocs.io/index.html) ** *ipyrad* **. El genoma de referencia obtenido corresponde a <span style="color:green">*Sebastes steindachneri*</span>. Este pez pertenece al mismo orden que *Acanthurus*, y es la especie más cercana con genoma disponible. Las relaciones filogéneticas pueden apreciarse en la [Filogenia](https://github.com/AridaiHari/Proyecto-Final-BioInfo-2018_II/blob/master/Filogenia%20Sebastes.png).

 La idea original fue realizar tres ensamblados diferentes uno con cada una de las especies y otro con las dos especies juntas; para diferenciar SNPs que permitan separar ambas especies por un lado, y por otro, diferenciar grupos genéticos al interior de cada especie. Se probaron en cada caso distintos parámetros de filtrado, para garantizar los polimorfismos verdaderos y omitir la mayor cantidad posible de datos faltantes.  Para visualizar los ensmblados y estimar el porcentaje de Missing data utilizamos ** *Tassel 5* **.
 
 Sin embargo, seguimos corriendo pruebas de ensamblado para el set de datos que incluye las dos especies pues tenemos *30% de missing data*.

- - -
#### 3. Análisis exploratorios
Se realizó para cada set de datos un análisis de componentes principales (*PCA*) utilizando la paquetería de **R *(SNPRelate)* **. Adicionalmente se realizó un análisis discriminante de componenentes principales (*DAPC*) con la paquetería de **R *(adegenet)* **.

En <span style="color:purple">*A. reversus*</span>, considerando todos los componentes y en concordancia con el artículo, encontramos un grupo genético **K=1** (valor mas bajo de Akaike =*50.88*) correspondiente a la isla de Las Marquesas. También se realizó el análisis con *K=2*, el segundo valor mas bajo (*AIC=51.47*), donde observamos que dos individuos estan más diferenciados del resto y son agrupados juntos reiteradamente.


ePara el caso de <span style="color:red">*A. olivaceus*</span>,en coincidencia con el articulo y considerando los componentes que explican al menos el 85% de la variacion, encontramos un grupo genético **K=1** (*AIC=252.3114*). Considerando solo el 80% de la varicaión, el DAPC determinó dos grupos *(K=2)*. Sin embargo, no pudimos determinar a cual de las 6 islas pertenecen estas muestras porque los ID de los individuos utilizados para los análisis genómicos no aparecen dentro de los [sitios de colecta](https://datadryad.org/bitstream/handle/10255/dryad.81059/Sample_database.xlsx?sequence=1), lo que genera un problema de reproducibilidad.


---
#### 4. Análisis de agrupamiento

Pasamos una semana instalando primero el sofware FastStructure pero tuve problemas con la instalación de algnas de sus dependencias, asi que decídi probar con el software ==FineStructure=. Tambien tuvimos algunos problemas instalando las dependencias pero al final lo logramos con éxito.Sin ambergo, he tenido algunos problemas para correrlo. Pienso terminar las gráficas, hacer el README, terminar el reporte, antes de seguir intentando correr el programa, e incluirlo solo si me da tiempo. Y hacer todos los análisis con el set de datos de ambas especies, en cuanto salga un ensamblado y llamado de SNPs decente.


---
#### 5. Heterocigocidad y H-W

Para calcular equilibrio de Hardy-Weinberg, riqueza alélica, heterocigocidad observada, heterocigocidad esperada y desequilibrio de ligamiento por locus y por individuos utilizamos la imagen **Biocontainers *VCFTOOLS* **.