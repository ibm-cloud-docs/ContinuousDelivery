---

copyright:
  years: 2018, 2019
lastupdated: "2019-05-31"

keywords: secure environment, data, IBM Cloud Continuous Delivery, Data

subcollection: ContinuousDelivery

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen:.screen}
{:codeblock:.codeblock}


# Protección de los datos    
{: #cd_data_security}  

{{site.data.keyword.contdelivery_full}} aloja las bases de datos en un entorno seguro y de alta disponibilidad:
   * Los datos se cifran en reposo (GPFS, LUKS e incorporados en disco) y en curso (HTTPS y SSH). Las credenciales de sistema y de cliente se almacenan en discos cifrados.
   * La aplicación y los datos están configurados para la alta disponibilidad.
   * El acceso a los datos está limitado a solo aquellos usuarios que necesitan los datos para dar soporte y mantener el servicio.
