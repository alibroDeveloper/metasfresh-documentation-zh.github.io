---
title: I_Product
layout: default
tag: 
   - Data Migration
lang: en
---

## Example


```

insert into i_product (i_product_id,ad_client_id,ad_org_id,isactive,created,createdby,updated, updatedby, i_isimported, value,name,
                       description,documentnote,productcategory_value,x12de355, c_taxcategory_name,m_pricelist_version_name, pricestd )
     (
	select
        nextval('i_product_seq'),
		1000000,
		1000000,
		'Y',
		now(),
		100,
		now(),
		100,
		'N',
		'value / key of product,
		'name of product',
		'description',
		'text for documentnote',
		'value of product category',        
        'x12 name of UOM',
        'name of tax category',
        'name of pricelistversion',
        123 --pricestd
  FROM migration_data.<yourtablename> 
  
```
