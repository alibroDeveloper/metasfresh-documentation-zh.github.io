---
layout: default
title: Troubleshooting SQL Update Process (sqlmigrate) 
tags:
  - Troubleshooting Server Update
lang: en
---

## Issue
When trying to update to a new version, errors on the app server may occur similar to the following:

## Error - Key (ad_name_id)=(1003093) is not present in table "ad_element"
```
app_1             |     psql:/opt/metasfresh/dist/sql/10-de.metas.adempiere/5516940_sys_gh5070-discount-schema-lines-window.sql:0: ERROR:  insert or update on table "ad_field" violates foreign key constraint "adname_adfield"
app_1             |     DETAIL:  Key (ad_name_id)=(1003093) is not present in table "ad_element".
```

**Workaround**
Add the missing element that was referenced by `ad_name_id` by getting the record from another database:

```sql
INSERT INTO public.ad_element (ad_element_id, ad_client_id, ad_org_id, isactive, created, createdby, updated, updatedby, columnname, entitytype, name, printname, description, help, po_name, po_printname, po_description, po_help, widgetsize, commitwarning, webui_namebrowse, webui_namenewbreadcrumb, webui_namenew) VALUES (1003093, 0, 0, 'Y', '2018-10-15 15:04:04.943585 +02:00', 99, '2018-10-15 15:04:04.943585 +02:00', 99, null, 'D', 'Kommentar/Hilfe', 'Kommentar/Hilfe', 'Comment or Hint', 'The Help field contains a hint, comment or help about the use of this item.', null, null, null, null, null, null, null, null, null);

```

---

## Error - ad_tab_id = Key (ad_tab_id)=(540877) already exists
```
app_1             |     psql:/opt/metasfresh/dist/sql/76-de.metas.vertical.creditscore.creditpass/5518780_sys_gh5016_add_missing_AD_Element_Link_records.sql:1: NOTICE:  2172 records added for missing AD_Fields
app_1             |     CONTEXT:  SQL statement "SELECT AD_Element_Link_Create_Missing_Field()"
app_1             |     PL/pgSQL function ad_element_link_create_missing() line 5 at PERFORM
app_1             |     psql:/opt/metasfresh/dist/sql/76-de.metas.vertical.creditscore.creditpass/5518780_sys_gh5016_add_missing_AD_Element_Link_records.sql:1: ERROR:  duplicate key value violates unique constraint "ad_element_link_uniquetab"
app_1             |     DETAIL:  Key (ad_tab_id)=(540877) already exists.

```

**Workaround**
```sql
select migrationscript_ignore('76-de.metas.vertical.creditscore.creditpass/5518780_sys_gh5016_add_missing_AD_Element_Link_records.sql')
```

---

## Error - Key (ad_table_id, columnname)=(114, Companyname) already exists
```
   psql:/opt/metasfresh/dist/sql/10-de.metas.adempiere/5518990_sys_gh5121_AddSeparateColumnsForCompanyValueAndNameAndCompanyNameFilter.sql:4: ERROR:  duplicate key value violates unique constraint "ad_column_name"
app_1             |     DETAIL:  Key (ad_table_id, columnname)=(114, Companyname) already exists.
```

**Workaround**
```sql
update ad_column set columnname = 'Companyname_2' where columnname='Companyname' and ad_table_id=114 ;

```

---

## Error - could not create unique index "c_postal_unique"
```
app_1             |     psql:/opt/metasfresh/dist/sql/10-de.metas.adempiere/5521480_sys_gh5192_C_Postal_UniqueIndex.sql:19: ERROR:  could not create unique index "c_postal_unique"
app_1             |     DETAIL:  Key (c_country_id, postal, (COALESCE(city, ''::character varying)), (COALESCE(township, ''::character varying)))=(107, 7556, Ramosch, ) is duplicated.
```

**Workaround**
```sql
select migrationscript_ignore('10-de.metas.adempiere/5521480_sys_gh5192_C_Postal_UniqueIndex.sql');
```

---

## Error - Key (ad_tab_id)=(540877) already exists
Occurring after SQL migration is done:

```
psql:/tmp/after_migration.1528556815613020924.sql:1: ERROR:  duplicate key value violates unique constraint "ad_element_link_uniquetab"
app_1             |     DETAIL:  Key (ad_tab_id)=(540877) already exists.
```

**Workaround**
```sql
delete from ad_element_link where ad_tab_id = 540877;
```



# Docker Commands

Update to 5.112

```BASH
docker exec  -u postgres <dev> psql -d metasfresh -c "INSERT INTO public.ad_element (ad_element_id, ad_client_id, ad_org_id, isactive, created, createdby, updated, updatedby, columnname, entitytype, name, printname, description, help, po_name, po_printname, po_description, po_help, widgetsize, commitwarning, webui_namebrowse, webui_namenewbreadcrumb, webui_namenew) VALUES (1003093, 0, 0, 'Y', '2018-10-15 15:04:04.943585 +02:00', 99, '2018-10-15 15:04:04.943585 +02:00', 99, null, 'D', 'Kommentar/Hilfe', 'Kommentar/Hilfe', 'Comment or Hint', 'The Help field contains a hint, comment or help about the use of this item.', null, null, null, null, null, null, null, null, null);"

docker exec  -u postgres <dev> psql -d metasfresh -c "select migrationscript_ignore('76-de.metas.vertical.creditscore.creditpass/5518780_sys_gh5016_add_missing_AD_Element_Link_records.sql')"

docker exec  -u postgres <dev> psql -d metasfresh -c "update ad_column set columnname = 'Companyname_2' where columnname='Companyname' and ad_table_id=114 ;"
docker exec  -u postgres <dev> psql -d metasfresh -c "select migrationscript_ignore('10-de.metas.adempiere/5521480_sys_gh5192_C_Postal_UniqueIndex.sql');"
docker exec  -u postgres <dev> psql -d metasfresh -c "delete from ad_element_link where ad_tab_id = 540877;"
```
