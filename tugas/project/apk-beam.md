<div id="header" width="30%" align="center">
    <img src="../../asset/beam-ds.png" width="30%%" />
    <p>Psuedocode Aplikais Beam</p>
</div>


---
### Welcome Page
---

Psuedocode
```
    procedure login_Option

    procedure pageWelcome

    begin 

        boolean Click 
        accept Click
        
        display "Selamat datang di Beam & Lanjutkan ke login"
        display "Tombol : Lanjutkan untuk login"

        if(Click = true)
            begin 
                display "Lanjutkan untuk login "
                call login_Option
            end
        else
            begin 
             call pageWelcome
            end
        endif

    end
```

Flowchart : 


---
### OPTION LOGIN PSUEDOCODE

```
    function funLogin_Phone

    procedure login_Option
    begin 
        boolean statusKlik = true
        accept statusKlik
        switch(loginGoogle, numberPhone)
            begin 
                case loginGoogle : 
                    call proLogin_Google
                    break
                case numberPhone : 
                    call funLogin_Phone   
                    break
                default : 
                    display "Pilih Opsi Login yang ingin digunakan"
                    
            end
    end
```
---
### LOGIN GOOGLE ACOUNT
```

    character nGmail, nPassword 

    compute nGmailDatabase as (nGmail, nPassword)

    function proLogin_Google
    begin
    
        character nAccountGoogle 
        

        label BackSelectGmail: 
            display "ERROR : Harap menggunakan account yang terdaftar dengan gmail anda"

        display "Silahkan pilih akun google untuk melanjutkan ke beam"
        accept nAccountGoogle
        display nAccountGoogle
        
        compute nAccountGoogleSelected as (nAccountGoogle)

        if(nAccountGoogleSelected == nGmailDatabase )
            begin
                if(nAccountGoogleSelected == nGmail)
                    begin 
                        call mainPage
                    end
                else
                    begin 
                        display "Akun ini tidak terdaftar "
                        goto BackSelectGmail
                    end
                endif
            end
        elseif(nAccountGoogleSelected != nGmailDatabase)
            begin 
                display nAccountGoogleSelected

                if(nAccountGoogleSelected == nGmail)
                    begin 
                        compute nGmailDatabase as (nAccountGoogleSelected)

                        call mainPage
                    end
                else
                    begin 
                        display "Akun ini tidak terdaftar dengan gmail anda"
                        goto BackSelectGmail
                    end
                endif
            end
        else
            begin 
                goto BackSelectGmail
            end
        endif
    end

```
---
### LOGIN PHONE NUMBER

Psuedocode : 
```
    character nPhoneDatabase, nPhone , nNationPhoneCode = +62

    compute nPhoneDatabase as (nPhone, nNationPhoneCode)

    function funLogin_Phone
    begin 
        
        label Error : 
            display "Harap periksa nomor anda kembali"

        display "Masukkan Kode No.Telpon anda gunakan "
        accept nNationPhoneCode

        display "contoh no.telfon : 81xx-xxx-xxx"
        accept nPhone
        

        // Di sini ada 2 kondisi dimana pada saat nPhone tidak ada, maka langsung terdaftar
        if(nInputData == nPhoneDatabase && nNationPhoneCode == nPhoneDatabase)
            begin 

                if(nNationPhoneCode == "+62") 
                    begin 
                        character nKode
                        accept nVerify
                        compute nVerify as (nKode)

                        display nVerify

                        //Diterima dan di kirim ke database, langsung menuju mainPage
                        accept nPhoneDatabase
                        
                        call mainPage
                    end
                else 
                    begin 
                        goto Error
                    end
                endif
            end
        elseif (nInputData != nPhoneDatabase && nNationPhoneCode != nPhoneDatabase)
            begin 
                if(nNationPhoneCode == "+62")
                    begin 
                        character nKode
                        compute nVerify as (nKode)

                        display nVerify

                        //Simpan ke database dan menuju mainPage
                        compute nDatabase as (nNationPhoneCode + nPhone)
                        call mainPage
                    end
                else 
                    begin 
                        goto Error
                    end
                endif
            end
        else 
            begin 
                goto Error
            end
        endif
    end

```



---
### MAIN PAGE

```

    procedure mainPage
    begin 
        character nUser 
        numeric nBeamNear, nBeamId, nBeamBattery, nBeamTraveled ,nBeamTrack, nTarif, nHargaBuka
        boolean nStatusklik = true
        accept nUser, nBeamNear, nBeamId, nBeamBattery, nBeamTraveled ,nBeamTrack, nTarif, nHargaBuka

        display mainPage

        switch (nFitur )
            begin 
                case main : 
                    display nBeamNear

                    <!-- Label (ntar nanyak ) -->
                    label beamNear: 
                        display nBeamNear


                    while (nBeamNear == nStatusklik) // Di Klik
                        begin 
                            display nBeamId, nBeamBattery, nBeamTraveled, nTarif, nHargaBuka
                            boolean statusBerkendara = true

                            display "Pindai Untuk Berkendara?"
                            accept statusBerkendara 
                            
                            if(nUser == statusBerkendara)
                                begin 
                                    call nQrCode
                                end
                            else
                                begin 
                                    goto beamNear
                                end
                            endif
                        end
                    
                    goto beamNear
                    
                    break
                
                case Pembayaran : 
                    call proPembayaran
                    break
                case QRCode : 
                    call nQrCode
                    break
                case Account : 
                    call proAccount
                    beak
                default : 
                    display mainPage
            end
    end
```

### Top Up Saldo 
```
    // procedure input kartu kredit atau debit
    procedure InputKartu (input numeric, input numeric, input numeric, input character)

    //procedure untuk Active kan 
    proceudre Active (input character, input numeric, input numeric, input character)


    procedure proTopUp 
    begin 
        character nMethodPayment
        numeric nSaldo,nTopUp, nNominal , nDatabasePromo, nKartu
        accept nSaldo, nMethodPayment, nNominal,nTopUp, nDatabasePromo, nKartu

        display nSaldo 

        switch(nMethodPayment, nTopUp)
            begin 
                case IsiUlangSaldo : 

                    label nError : 
                        display "Harap periksa pilihan nominal dan nominal top up anda"

                    display "Pilih MethodPembayaran"
                    display "1. Kartu Kredit "
                    display "2. Shoope Pay "
                    display "3. Dana  "
                    display "4. OVO "
                    accept nMethodPayment

                    if(nMethodPayment == "1")
                        begin 
                            numeric nNomorKartu, nExpiredDate, nCVV, 
                            character nNameOwner
                            
                            if(nKartu == "")
                                begin 
                                   call Active (nNomorKartu, nExpiredDate, nCVV, nNameOwner)

                                    label kartuError : 
                                        display "harap periksa kembali kartu anda"

                                   call InputKartu (nNomorKartu, nExpiredDate, nCVV, nNameOwner)

                                   display "simpan kartu debit"

                                   if(InputKartu == true )
                                        begin 
                                            call mainPage
                                        end
                                    else
                                        begin 
                                            goto kartuError
                                        end
                                    endif
                                end
                            else 
                                begin 
                                    numeric nNomimal
                                    boolean nStatus = true
                                    display "Masukkan jumlah top up"
                                    accept nNominal

                                    display "Confirm Payment in Your Card"

                                    if(nTopup == nNominal)
                                        begin 
                                            display "Pembayaran Berhasil"
                                            call mainPage
                                        end
                                    else 
                                        begin 
                                            goto nError
                                        end
                                    endif
                                end
                            endif

                            call mainPage
                        end
                    elseif(nMethodPayment == "2")
                        begin 
                            boolean ApkShoopie = true, nStatus = false
                            accept AphkShoopie, nStatus

                            display "Confirm Payment in Shoopie Pay"

                            while (ApkShoopie == true)
                                begin 
                                    if(nStatus == "terbayarkan")
                                        begin 
                                            display "Saldo beam anda sudah terisi"

                                            call mainPage
                                        end
                                    elseif (nStatus == "pending")
                                        begin 
                                            display "Harap tunggu beberapa saat"                                            
                                        end
                                    else 
                                        begin 
                                            display "Harap kirimkan bukti pembayaran anda di bawah kolom ini"
                                        end
                                    endif
                                end 
                            
                            call mainPage
                            
                        end
                        
                    elseif(nMethodPayment == "3")
                        begin 
                            numeric nApkDana, nPhoneNumber, nNetwork 
                            boolean nPin = false

                            label InputNomorSalah: 
                                display "Masukkan Nomor telfon anda dengan benar"

                            display "Input Nomor Dana Anda"

                            accept  nApkDana, nPhoneNumber, nNetwork ,nPin

                            if(nPhoneNumber == true)                    
                                begin 
                                    
                                    label nErrorPin : 
                                        display "Input pin dengan benar"

                                    display "Input pin anda"
                                    
                                    
                                    if(nPin == true )
                                        begin 

                                            label internetLagging: 
                                                display "Internet terlalu rendah, harap mencoba ulang"

                                            display "Proses pembayaran akan sebentar lagi"
                                            
                                            // Ini di situasi tertentu saja, jadi kalau internet bermasalah
                                            if(nNetwork == "not stable")
                                                begin 
                                                    goto internetLagging // internet bermasalah langsung ke label internetLagging
                                                end
                                            else 
                                                begin 
                                                    display "Pembayaran sukses"
                                                end
                                            endif             
                                        end
                                    else 
                                        begin 
                                            goto nErrorPin
                                        end
                                    endif

                                    call mainPage
                                end
                            else
                                begin 
                                    goto InputNomorSalah
                                end
                            endif

                        end
                    elseif(nMethodPayment == "4")
                        begin 
                            numeric nApkOvo, nPopuP, nPin, nSaldoOvo, 
                            boolean nSelect = true

                            accept nApkOvo, nPopuP, nPin, nSaldoOvo

                            display "Kami akan mengirimkan pop up untuk konfirmasi pembayaran"

                            display nPopUp

                            if(nPopUp == nSelect) // ketika user klik pop upnya
                                begin 

                                    numeric nAvg
                                    boolean nConfirm = false

                                    display nNominal

                                    label nFalsConfirm: 
                                        display "harap coba lagi"

                                    display "Harap konfirmasi pembayaran"
                                    accept nConfirm

                                    

                                    if(nConfirm == true )
                                        begin 
                                            if(nSaldo >= nNominal)
                                                begin 
                                                    compute nAvg as (nNominal - nSaldo)
                                                    display nAvg

                                                    display "pembayran telah berhasil"

                                                    call mainPage
                                                end
                                            else 
                                                begin 
                                                    display "Harap isi terlebih dahul saldo anda"
                                                    call proPembayaran
                                                end
                                            endif
                                        end
                                    else
                                        begin
                                            goto nFalsConfirm
                                        end
                                    endif
                                end
                            endif
                        end
                    else
                        begin 
                            call mainPage
                        end
                    endif
                    
                    break
                default : 
                    display "This is payment page and you can add payment method in here "
                    call proPembayaran

            end
        
    end

```
---
### QR CODE & DAN PENYEWAAN BEAM SEKALIGUS PEMBAYARAN

```
procedure QrCode
begin 
    numeric nQRID, nBeamID, nWaktu, nTarif, nSaldo
    bolean statusHelm = true, BeamStatus = false 

    label qrError: 
        display "QR Beam dan ID Beam tidak cocok, harap coba lagi"

    display "Scan QR Pada Beam"
    accept nQRID, nBeamID, nWaktu, nTarif, statusHelm, BeamStatus, nSaldo

    if (nQrID == nBeamID )
        begin 
            if(nSaldo >= 20000)
                begin 
                    label DisplayPerjalanan : 
                        Display "Anda sedang dalam perjalanan"

                    display BeamStatus, nTarif, nWaktu
                    
                    boolean statusPerjalan = false
                    
                    display "Button : Akhiri Perjalanan?"

                    accept statusPerjalan

                    if(statusPerjalan == true)
                        begin 
                            numeric nHargaTotal, nHargaBuka = 1750, nWaktuMenit 
                            boolean statusHelm = false
                            accept nHargaTotal, nHargaBuka, nWaktuMenit

                            display "Silahkan kembalikan helm ke tempatnya"

                            accept statusHelm

                            if(statusHelm == true)
                                begin 
                                    goto ComputeAkhir
                                end
                            else
                                begin 
                                    goto DendaHelm
                                end
                            endif
                            
                            label DendaHelm: 

                            label ComputeAkhir: 
                                compute nHargaTotal as ( nHarga * nWaktuMenit + nHargaBuka ) 

                                numeric nTarifAkhir
                                accept nTarifAkhir

                                compute nTarifAkhir as ( nSaldo - nHargaTotal )
                                display nTarifAkhir


                            label DendaHelm : 
                                compute nHargaTotal as ( nHarga * nWaktuMenit + nHargaBuka ) 
                                
                                numeric nTarif ,nDendaHelm ,nHargaDendaHelm = 75000
                                accept nTarif, nDendaHelm ,nHargaDendaHelm

                                compute nDendaHelm as (nHargaDendaHelm + nHargaTotal )
                                compute nDendaHelm as (nSaldo - nDendaHelm)

                                display nDendaHelm

                            
                            call mainPage


                        end
                    else 
                        begin 
                            goto DisplayPerjalanan
                        end
                    endif
                end
            else
                begin 
                    display "Saldo harus di atas Rp 20.000"
                    call proPembayaran
                end
            endif
        end
    else
        begin
            goto qrError
        end
    endif
end
```


--- 

### AKUN DAN RIWAYAT
```
    procedure proAccount
    begin 
        character cEmail, cfirstName, cLastName, cOption, cHapusAkun
        accept cEmail, cfirstName, cLastName, cOption, cHapusAkun
    
        display "1. Profile"
        display "2. Riwayat Berkendara"

        switch(nOption)
            begin 
                case 1 :    

                    label nDisplayProfile: 
                        display "Ini Adalah profile anda"

                    display cEmail, cfirstName, cLastName,
                    
                    boolean nStatusOptionHapusAkun = false
                    accept nStatusOptionHapusAkun

                    if( nStatusOptionHapusAkun == true )
                        begin 
                            character cOptionAlasan

                            // display alasan menghapus akun anda
                            display "Input alasan mengapa menghapus akun anda"

                            accept cOptionAlasan 

                            call pageWelcome
                        end
                    else 
                        begin 
                            goto nDisplayProfile 
                        end
                    endif

                    break

                case 2 : 
                    character cTanggal, cPukul, cWaktu, cDurasi, cPaymentMethod, cRiwayatDetailButton, cRiwayat, cResiDetail
                    numeric nTotalHarga
                    boolean statusKlik = false
                    accept cTanggal, cPukul, cWaktu, nTotalHarga, cDurasi, statusKlik, cPaymentMethod, cRiwayatDetailButton, cRiwayat, cResiDetail

                    // ini merupakan cRiwayat biasa
                    compute cRiwayat as ( cTanggal, cPukul, cWaktu, nTotalHarga, cDurasi) 
                    
                    label nBackRiwayat:
                        display "Riwayat Terakhir anda"

                    display cRiwayat

                    display "Detail Resi Perjalanan"

                    while( statusKlik == true)
                        begin 
                            display "berikut detail perjalanan"
                            display cWaktu, nTotalHarga, 
                        end

                    call proAccount

                    break
                
                default: 
                    display "Ini adlaah page profile anda"
                    call proAccount
            end
        

    end
```

--- 
