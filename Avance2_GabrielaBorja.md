
# Trabajo final Gabriela Aridai Borja Martínez.

## BioinfoRepro2018-II

*****

#### *Sistema de trabajo:*

Dado que la coloración es una característica sujeta a selección que puede conducir a aislamiento reproductivo. La sitemática tradicional frecuentemente utiliza variaciones de color como caracteres que permiten la identificación de especies. Buscando **señales de aislamiento y selección** se analizaron dos especies del género *Acanthurus*, del complejo de especies de los epces cirujanos (*Surgeonfish*): <span style="color:red">*Acanthurus olivaceus*</span> y <span style="color:purple">*Acanthurus reversus*</span>. El primero se distribuye en el Pacífico Central y Hawai, mientras que el segundo en Las Marquesas.

Los datos **RAD-seq** trabajados para este proyecto fueron obtenidos del repositorio de datos Dryad.

Gaither MR, Bernal MA, Coleman RR, Bowen BW, Jones SA, Simison WB, Rocha LA (2015)  [Genomic signatures of geographic isolation and natural selection in coral reef fishes.](http://doi.org/10.1111/mec.13129) Molecular Ecology 24(7): 1543-1557.

Gaither MR, Bernal MA, Coleman RR, Bowen BW, Jones SA, Simison WB, Rocha LA (2015) [Data from:](http://doi.org/10.5061/dryad.581f3) Genomic signatures of geographic isolation and natural selection in coral reef fishes. Dryad Digital Repository.

Este trabajo tiene como objetivo implementar algunos de los análisis bioinformáticos realizados en el artículo previamente citado. Dichos análisis se realizarán en un software  diferente para poder realizar una comparación con los análisis originales. Los análisis se documentarán de forma adecuada para garantizar su **reproducibilidad.**

El trabajo se encuentra organizado en los siguientes *directorios*:
- `bin` Contiene los scripts con los pipeline utilizados para cada software en las distintas etapas de análisis.
- `Data` Contiene los inputs requeridos y outputs generados por cada  software organizados en sus respectivos directorios
- `Plots` contiene todas las figuras y gráficas generados.

- - -
#### 1.Filtrado de calidad

Pese a que las secuencias descargadas se reportan como filtradas y desmultiplexeadas, se verificó la calidad de las secuencias usando la imagen de ==Biocontainers *Fastqc*==. Todas las muestras, tanto de <span style="color:purple">*A. reversus*</span> como de <span style="color:red">*A. olivaceus*</span> presentaron las bases **3 y 4** fuera de los estándares de calidad, por lo que fueron eliminadas utilizando ==Biocontainers *fastxtools*==. Posiblemente esto se deba a que los adaptadores no fueron removidos.

- - -
#### 2. Ensamble con genoma de referencia
Actualmente nos encontramos realizando un ensamblado con **genoma de referencia**. El genoma obtenido corresponde a <span style="color:green">*Sebastes steindachneri*</span>, el cual pertenece al mismo orden de peces. Es la especie mas cercana con genoma disponible. Las relaciones filogenéticas pueden apreciarse en la [Filogenia](https://github.com/AridaiHari/Proyecto-Final-BioInfo-2018_II/blob/master/Filogenia%20Sebastes.png). El ensamblado se realizará con ==*ipyrad*==. El software y sus dependencias han sido instaladas con éxito.

- - -
### Pasos siguientes:
1. Llamado de SNPs
2. Genotipificación
3. Estadísticos de diversidad genética
4. Análisis exploratorios (DAPC(adegenet))
5. Análisis de clustering (Finestructure o FastSTRUCTURE)

##### Notas:
Cada especie se esta trabajando por separado. Pero en ambas vamos en el mismo paso. Los estadísticos y análisis de agrupamiento se harán con las especies por separado, y con las especies juntas como una sola población.

En mi proyecto utilizaré un genoma de referencia, por tanto aunque no hay genoma de referencia para *Acanthurus*, Alicia y yo llegamos al acuerdo de realizarlo con genoma de referencia de alguna especie no cercanamente relacionada.

 instalamos con éxito PGDSpider para convertir a los inputs a los formatos requeridos para cada software.

