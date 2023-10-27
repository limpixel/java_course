## Welcome to Tugas Pak Tom :smile:


- Buatlah psuedocode dan flowchart untuk aplikasi kalkulator sederhana (+,-,/,*)
- Tampilkan fitur kalkulator pada user 
- Lakukan sesuai fiturnya dan selesai dengan fitur yang ada
- Setelah User melakukan fitur, mau make lagi kalkulator nya dan kalau mau tampilkan 
- END

---
# Tricky : 
- [1] Hati-hati pada fitur pembagian karena kalau pembaginya 0 maka munculkan display " tidak bisa bisa dibagi"
- [2] mau mengulangi kalkulator Y dan N, menggunakan character khusus 

---

# HASIL TUGAS : 

```
begin 
    numeric nAngka1, nAngka2, nResult, nPilihan = "Yes"

    
    display "Silahkan Masukkan Input"

    Welcome1: 
        display "Silahkan Masukkan Input"

    accept nAngka1, nAngka2, nResult, nPilihan

    switch (nAngka1, nAngka2, nResult)
        begin 
            case penjumlahan : 

                compute nResult as (nAngka1 + nAngka2) 

                display "Hasil :" nResult "Dan Masih ingin menggunakan Kalkulator?"

                if(nPilihan == "Yes" ) 
                    begin 
                        goto Welcome1
                    end
                else 
                    display "Terima kasih sudah menggunakna kalkulator"
                endif

                

            break

            case pengurangan : 
                compute nResult as (nAngka1 - nAngka2) 

                display "Hasil :" nResult "Dan Masih ingin menggunakan Kalkulator?"

                if(nPilihan == "Yes" ) 
                    begin 
                        goto Welcome1
                    end
                else 
                    display "Terima kasih sudah menggunakna kalkulator"
                endif

            break

            case perkalian : 
                compute nResult as (nAngka1 * nAngka2) 

                display "Hasil :" nResult "Dan Masih ingin menggunakan Kalkulator?"

                if(nPilihan == "Yes" ) 
                    begin 
                        goto Welcome1
                    end
                else 
                    display "Terima kasih sudah menggunakna kalkulator"
                endif
            break

            case pembagian : 
                
                KembaliInputBagi: 
                    display "Tidak bisa di bagi dan harap masukkan angka dengan benar"

                if(nAngka1 == 0 OR nAngka == 0)
                    begin
                        goto KembaliInputBagi                         
                    end
                else
                    begin 
                        compute nResult as (nAngka1 / nAngka2) 
                    end
                endif

                display "Hasil :" nResult "Dan Masih ingin menggunakan Kalkulator?"

                if(nPilihan == "Yes" ) 
                    begin 
                        goto Welcome1
                    end
                else 
                    display "Terima kasih sudah menggunakna kalkulator"
                endif

            break

            default : 
                display "Terima Kasih sudah menggunakan kalkulator"

        end
    end 

end 
```

<!-- 
## TUGAS 
begin 
    numeric nAngka, nResult,  
    display "Masukkan Input"
    accept nAngka, nResult,  


    switch 
        begin 
            case penjumlahan : 
            case pengurangan : 
            case perkalian : 
            case pembagian : 
        end
    end 

end 

 -->