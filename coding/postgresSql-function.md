```sql
CREATE OR REPLACE FUNCTION query_result(IN inputDate text) RETURNS TABLE 
(aa varchar(64),ss varchar(64),n timestamp)AS $$

declare counter integer:=1;
declare startTime timestamp:=to_timestamp(inputDate, 'yyyy-MM-dd hh24:mi:ss');
declare days integer:=(select extract (day from date_trunc('month', startTime)+ interval '1 month'- interval '1 day'));

begin
	
	while counter<days loop
        counter := counter + 1;
       	return query
    	select  distinct xx,xx,xx from xxx   where  condition1 and
    	and xxx >=to_timestamp(to_char(startTime,'yyyy-mm-')||to_char(counter,'00') ||' 00:00:00','yyyy-MM-dd hh24:mi:ss' )
    	and xxx <=to_timestamp(to_char(startTime,'yyyy-mm-')||to_char(counter,'00') ||' 23:59:59','yyyy-MM-dd hh24:mi:ss' );
    end loop;
END;
$$ LANGUAGE plpgsql STABLE;

SELECT * FROM query_result('2023-02');              

```