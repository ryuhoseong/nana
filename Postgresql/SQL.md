### 재귀쿼리
```
with recursive ref_view as (
select
	code,
	code_name,
	parent_code,
	cast(code as varchar(1000)) AS parents,
	array[code]::varchar[] AS codes
from
	code_tbl parent_tbl
where
	code = '[최상위 code]'
--  parent_code is null
union all
select
	child_code.code,
	child_code.code_name,
	child_code.parent_code,
	cast(ref_view.parents || ', ' || child_code.code as varchar(1000)) AS parents,
	ARRAY_APPEND(ref_view.codes, child_code.code) AS codes
from
	code_tbl child_code
inner join ref_view on ref_view.code = child_code.parent_code
)
select
	*, codes[1]
from
	ref_view
;
```