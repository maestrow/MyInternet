## T-Sql

### Создание БД

	CREATE DATABASE FileSystemMeta
	ON 
		PRIMARY (NAME = FileSystemMeta, FILENAME = 'z:\dbs\FileSystemMeta\FileSystemMeta.mdf'),
		FILEGROUP 
			FileStreamGroup CONTAINS FILESTREAM (NAME = FileSystemMetaFilestream, FILENAME = 'z:\dbs\FileSystemMeta\Filestream')
		LOG ON (NAME = FileSystemMetaLog, FILENAME = 'z:\dbs\FileSystemMeta\FileSystemMeta.ldf')
	WITH 
		FILESTREAM ( NON_TRANSACTED_ACCESS = FULL, DIRECTORY_NAME = 'FileSystemMeta' )
	GO


### Создание таблицы

	CREATE TABLE books AS FileTable WITH (FILETABLE_STREAMID_UNIQUE_CONSTRAINT_NAME = ui_file_stream)


### Присоединение (Attach) базы данных с Filestream

	CREATE DATABASE FileSystemMeta
	ON 
		(FILENAME = 'z:\dbs\FileSystemMeta\FileSystemMeta.mdf'),
		(FILENAME = 'z:\dbs\FileSystemMeta\FileSystemMeta.ldf'),
		FILEGROUP 
			FileStreamGroup CONTAINS FILESTREAM (NAME = FileSystemMetaFilestream, FILENAME = 'z:\dbs\FileSystemMeta\Filestream')
	FOR ATTACH

## FAQ

- Q: есть ли готовые front-end'ы? A: Не нашел
- Q: как добавить существующие директории и диски к FileTable? A: [You cannot convert an existing folder to a FileTable](http://msdn.microsoft.com/en-us/library/gg492083.aspx).

## Ссылки

- [Processing nonstructured data using FILESTREAM and FileTable](http://sqlblog.com/blogs/john_paul_cook/archive/2013/09/07/processing-nonstructured-data-using-filestream-and-filetable.aspx) by John Paul Cook.
