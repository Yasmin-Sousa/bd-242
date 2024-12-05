
@startuml
entity TB_MEDIA_TYPES{
*MediaTypeId:INTEGER
Name:NVARCHAR(120)
}
entity TB_GENRES{
*GenreId:INTEGER
Name:NVARCHAR(120)
}
entity TB_PLAYLISTS{
*PlaylistId:INTEGER
Name:NVARCHAR(120)
}
entity TB_PLAYLISTS_TRACK{
*PlaylistId:INTEGER
--
*TrackId:INTEGER
}
entity TB_TRACKS{
*TrackId:INTEGER
--
Name:NVARCHAR(200)
--
AlbumId:INTEGER
--
MediaTypeId:INTEGER
--
GenreId:INTEGER
--
Composer:NVARCHAR(220)
--
Milliseconds:INTEGER
--
Bytes:INTEGER
--
UnitPrice:NUMERIC
}
entity TB_ARTISTS{
*ArtistId:INTEGER
Name:NVARCHAR(120)
}
entity TB_INVOICES{
*InvoiceId:INTEGER
--
CustomerId:INTEGER
--
InvoiceDate:DATETIME
--
BillingAddress:NVARCHAR(70)
--
BillingCity:NVARCHAR(40)
}
entity TB_INVOICE_ITEMS{
*InvoiceItemId:INTEGER
--
InvoiceId:INTEGER
--
TrackId:INTEGER
--
UnitPrice:NUMERIC
--
Quantity:INTEGER
}
entity TB_ALBUMS{
--
*Albumld: INTEGER
--
Title: NVARCHAR(160)
--
Artistid: INTEGER
}
entity TB_CUSTOMERS{
*Customerld: INTEGER
--
FirstName: NVARCHAR(40)
--
LastName: NVARCHAR(20)
--
Company: NVARCHAR(80)
--
Address: NVARCHAR(70)
--
City: NVARCHAR(40)
--
State: NVARCHAR(40)
--
Country: NVARCHAR(40)
--
PostalCode: NVARCHAR(10)
--
Phone: NVARCHAR(24)
--
Fax: NVARCHAR(24)
--
Email: NVARCHAR(60)
--
SupportRepld: INTEGER
}
entity TB_EMPLOYEES{
*Employeeld: INTEGER
--
LastName: NVARCHAR(20)
--
FirstName: NVARCHAR(20)
--
Title: NVARCHAR(30)
--
ReportsTo: INTEGER
--
BirthDate: DATETIME
--
HireDate: DATETIME
--
Address: NVARCHAR(70)
}
TB_MEDIA_TYPES ||--o{ TB_TRACKS
TB_GENRES |o--o{ TB_TRACKS
TB_PLAYLISTS ||--o| TB_PLAYLISTS_TRACK
TB_PLAYLISTS_TRACK |o--|| TB_TRACKS
TB_ARTISTS ||--o{ TB_ALBUMS
TB_TRACKS }o--o| TB_ALBUMS
TB_TRACKS ||--o{ TB_INVOICE_ITEMS
TB_INVOICES ||--o{ TB_INVOICE_ITEMS
TB_INVOICES }o--|| TB_CUSTOMERS
TB_CUSTOMERS }o--o| TB_EMPLOYEES
TB_EMPLOYEES |o--o{ TB_EMPLOYEES
@enduml
