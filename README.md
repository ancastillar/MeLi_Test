# MeLi_Test

# **Contenido del Git**

* Imágentes de los resultados del modelo de clusterización (K-means)
* Notebook: Construcción del marco de datos, EDA y Modelo

# **Business Case**:
El equipo comercial quiere realizar estrategias focalizadas para los sellers, pero en
este momento no existe una clasificación que permita identificar a aquellos que tienen
un buen perfil y son relevantes para el negocio. ¿Cómo podrías ayudar al equipo
comercial a identificar estos sellers?

# **Solución**

**La solución del problema se focalizó únicamente en Mecado Libre Colombia**

## **¿Qué información buscaste y utilizaste para el desarrollo de la solución?**

Para la solución realicé un muestreo teniendo en cuenta la categoría de los items que actualmente se venden en Colombia. Para cada categoría se extraen los 1000 primeros datos que se encuentren a partir del request. De esta manera, nuestro marco de datos inicial consta de una dimensión 33510 datos 22 variables.

Posteriormente, de una exploración inicial general se encuentra que no hay información completa que permita identificar a los **sellers**, por tal motivo esta información se obtiene mediante otro request.

Finalmente, la información que se tiene para realizar el modelo consta de las siguientes variables:

* price_mean, 
* available_quantity_mean, 
* sold_quantity_mean,  
* listing_type_id_unique,
* condition_unique, 
* accepts_mercadopago_total, 
* order_backen_sum,
* quantity_help_pay_mean,
* rate_help_pay_mean,
* free_shipping_ship_sum, 
* logistic_type_ship_unique,  
* state_name_unique,p
* price_greater_reference_sum",
* name_unique, 
* diff_price_referenc_mean,
* pcte_price_amount_help_mean,
* sold_quantity_rate_mean,
* canceled_trans_selle_mean,	
* rate_cancell_seller_mean,	
* value_cancell_seller_mean,
* rate_claims_seller_mean,
* value_claims_seller_mean,	
* rate_delayed_seller_mean,
* value_delayed_seller_mean,	
* negative_rating_seller_mean,
* neutral_rating_seller_mean,
* positive_rating_seller_mean,	
* age_seller_months_mean,
* power_seller_status_seller_platinum,	
* power_seller_status_seller_silver,
* level_id_seller_2_orange,
* level_id_seller_3_yellow,
* level_id_seller_4_light_green,
* level_id_seller_5_green,

La información anterior se escogio ya que se quiere incluir tanto comportamiento general del sellers (ratings, reclamos, entre otros), como comportamiento medio del seller respecto a sus ventas (precio medio de sus productos, cantidad de categorías asociadas,)

## **Qué enfoque escogiste, y cómo la abordaste. ¿Qué metodologías aplicaste? ¿Qué métricas de evaluación utilizaste?**

Para la solución del problema se escogió un modelo no survisado, en este caso **K-means**. Con este modelo buscamos encontrar el número óptimo de segmentos de **sellers** que actualmente hay en MeLi. De esta manera el equipo comercial podrá desarrollar estrategias focalizadas para cada segmento.

El algorimo se evaluó para diferentes clusters = [ 2,4,5,6,7,8,9,10,11,12,13,14,15,16] y la cantidad de segmentos óptimos se escogió mediante la métrica de **Silhouette Coefficient**:  es una métrica utilizada para calcular la bondad de una técnica de clusterización. Su valor se encuentra entre -1 a 1.

* 1: Significa que los clusters están bien separados unos de otros y se distinguen claramente.

* 0: Los clusters de medios son indiferentes, o podemos decir que la distancia entre clusters no es significativa.

* -1: Los clusters de medios están asignados de forma errónea w

## **¿Cuál es tu solución final? ¿Cómo se comporta? ¿Cómo soluciona o ayuda a solucionar el problema de negocio?**

**Silhouette Coefficient**



![plot](./cluster_score.png)

El mejor score se encuentra para n_clusters = 4 (score=0.50). A continiación presentamos la distribución de la cantidad de sellers en cada segmento

![plot](./number_sellers_each_cluster.png)

