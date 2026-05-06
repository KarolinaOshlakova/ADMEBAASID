## SQL protseduur - 
store procedure - salvestatud protseduurid - sama mis on fumnktsoonid programmeerimises, mingi tegevus mis on salvestatud 
andmebaasi, ja mida saab automaatselt teha (INSERT, UPDATE, SELECT, DELETE).

```sql
--protseduur mis lisab andmeid tabelisse ja kohe kuvab neid.(INSERT, SELECT)
CREATE procedure lisaKategooria 
--parameetrid @...
@uusKategooria varchar(30)
AS
BEGIN
--kirjeldus	
	INSERT INTO categories(category_name)
	VALUES (@uusKategooria);
	SELECT * FROM categories;
END;
--kutse 
EXEC lisaKategooria 'Auto';
```
<img width="257" height="366" alt="{F64F09F6-182C-4C15-B672-301839077B72}" src="https://github.com/user-attachments/assets/ffe3dae3-792a-481e-ab59-d9f824956706" />

```sql

--protseduur, mis kustutab kategooria id järgi 
CREATE procedure kustutaKategooria
@kustutaId int
AS
BEGIN
	SELECT * FROM categories;
	DELETE FROM categories WHERE category_id=@kustutaId;
	SELECT * FROM categories;
END
-- kutse
EXEC kustutaKategooria 1
```
<img width="356" height="291" alt="{CCAAC61C-F432-47E7-A880-3E7ABB90610D}" src="https://github.com/user-attachments/assets/92c6bcf5-5236-4020-a173-97e1db37779c" />

```sql
--protseduur mis kuvab kategooriad sisestatud esimese tähte järgi 
-- процедуры которые показывает все процедуры по первой введенной букве
CREATE PROCEDURE otsing1taht
@taht char(1)
AS
BEGIN
	SELECT * FROM categories 
	WHERE category_name LIKE @taht + '%'; --% - teised sümboolid
END

--kutse 
EXEC otsing1taht 'A';
```
<img width="284" height="100" alt="{1213B838-1BF6-46E4-B436-EA9462B0ADDA}" src="https://github.com/user-attachments/assets/283b24ef-6627-4aa2-aff5-f65ca94295e6" />
