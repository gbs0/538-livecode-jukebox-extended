### Listar todos os clientes (nome + email), ordenados alfabeticamente (sem informações extras).

```sql
SELECT first_name, last_name, email FROM customers
ORDER BY last_name

```

### Listar todas as tracks (Nome + Compositor) da playlist de Clássicos

```sql
SELECT tracks.composer, tracks.name FROM playlist_tracks
JOIN tracks ON tracks.id = playlist_tracks.track_id
JOIN playlists ON playlists.id = playlist_tracks.playlist_id
WHERE playlists.name = "Classical"

```

### Listar os 10 artistas mais listados em todos as playlists

```sql
SELECT artists.name, COUNT(*) AS art_count FROM artists
JOIN albums ON artists.id = albums.artist_id
JOIN tracks ON albums.id = tracks.album_id
JOIN playlist_tracks ON tracks.id = playlist_tracks.track_id
GROUP BY artists.name
ORDER BY art_count DESC
LIMIT 10

```

### Listar as músicas que foram compradas pelo menos 2 vezes, ordenadas pelo número de compras.

```sql
SELECT tracks.composer, tracks.name, COUNT(*) AS compras FROM tracks
JOIN invoice_lines ON invoice_lines.track_id = tracks.id
GROUP BY tracks.id
HAVING compras >= 2
ORDER BY compras DESC

```
