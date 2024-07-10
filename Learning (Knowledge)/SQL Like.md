Sebelum Anda latihan langsung di SQL, berikut adalah pola yang dapat digunakan bersamaan dengan LIKE.

| Operator                       | Deskripsi                                                                                                                                              |     |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ | --- |
| WHERE (nama kolom) LIKE ‘a%’   | Mencari nilai apa pun pada field kolom yang dimulai huruf “a” atau Anda bisa menggunakan huruf lainnya.                                                |     |
| WHERE (nama kolom) LIKE ‘%a’   | Mencari nilai apa pun pada field kolom nama yang diakhiri huruf “a” atau Anda bisa menggunakan huruf lainnya.                                          |     |
| WHERE (nama kolom) LIKE ‘%or%’ | Mencari nilai apa pun pada field kolom yang di dalamnya terdapat huruf “or”. Anda juga bisa menggunakan huruf lainnya.                                 |     |
| WHERE (nama kolom) LIKE ‘_r%’  | Mencari nilai apa pun pada field kolom yang karakter keduanya huruf “r” atau Anda bisa menggunakan karakter lainnya.                                   |     |
| WHERE (nama kolom) LIKE ‘a_%’  | Mencari nilai apa pun pada field kolom yang dimulai dengan huruf “a” dan panjangnya minimal dua karakter atau Anda bisa menggunakan karakter lainnya.  |     |
| WHERE (nama kolom) LIKE ‘a__%’ | Mencari nilai apa pun pada field kolom yang dimulai dengan huruf “a” dan panjangnya minimal tiga karakter atau Anda bisa menggunakan karakter lainnya. |     |
| WHERE (nama kolom) LIKE ‘a%o’  | Mencari nilai apa pun pada field kolom yang dimulai huruf “a” dan diakhiri huruf “o” atau Anda bisa menggunakan karakter lainnya.                      |     |
