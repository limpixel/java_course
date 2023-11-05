<div id="header" width="30%" align="center">
    <img src="../../asset/beam-ds.png" width="30%%" />
    <p>Psuedocode Aplikais Beam</p>
</div>


---
### Welcome Page
---

Psuedocode
```
    procedure pageWelcome
    begin 
        character nOtpion
        boolean nStatusklik = true
        accept nOtpion, nStatusklik
        
        display "Selamat datang di Beam & Lanjutkan ke login"

        if(nOption == nStatusKlik)
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
    procedure login_Option
    begin 
        boolean statusKlik = true
        accept statusKlik
        switch(statusKlik)
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
                            display statusBerkendara = true ,nBeamId, nBeamBattery, nBeamTraveled, nTarif, nHargaBuka
                            display "Pindai Untuk Berkendara?"
                            
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


    procedure proPembayaran 
    begin 
        numeric nSaldo, nMethodPayment, nTopUp, nNominal ,nPromo, nDatabasePromo, nKartu
        accept nSaldo, nTopUp, nPromo, nDatabasePromo

        display nSaldo 

        switch(nMethodPayment, nTopUp, nPromo)
            begin 
                case IsiUlangSaldo : 

                    label nError : 
                        display "Harap periksa pilihan nominal dan nominal top up anda"

                    numeric paketKredit
                    display "Pilih Paket Kredit"

                    accept paketKredit

                    
                        

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

                                    label Error : 
                                        display "harap periksa kembali kartu anda"

                                   call InputKartu (nNomorKartu, nExpiredDate, nCVV, nNameOwner)

                                   display "simpan kartu debit"
                                   if(InputKartu == "true" )
                                        begin 
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
                                    display "Confirm Payment in Your Card"
                                    
                                    numeric nNomimal, nStatus = true


                                    if(nTopup == nNominal)
                                        begin 
                                            display "Pembayaran Berhasil"
                                        end
                                    else 
                                        begin 
                                            goto nError
                                        end
                                end
                        end
                    elseif(nMethodPayment == "2")
                        begin 
                            numeric ApkShoopie = true
                            accept AphkShoopie

                            numeric nStatus
                            display "Confirm Payment in Shoopie Pay"

                            while (ApkShoopie == true)
                                begin 
                                    if(nStatus == "terbayarkan")
                                        begin 
                                            display "Saldo beam anda sudah terisis"

                                            call proPembayaran
                                        end
                                    else if (nStatus == "pending")
                                        begin 
                                            display "Harap tunggu beberapa saat"                                            
                                        end
                                    else 
                                        begin 
                                            display "Harap kirimkan bukti pembayaran anda di bawah kolom ini"
                                        end
                                end 
                            
                        end
                        
                    elseif(nMethodPayment == "3")
                        begin 
                            numeric nApkDana, nPhoneNumber, nNetwork ,nPin = false

                            label InputNomorSalah: 
                                display "Masukkan Nomor telfon anda dengan benar"

                            display "Input Nomor Dana Anda"

                            accept  nApkDana, nPhoneNumber, nNetwork ,nPin

                            

                            if(nPhoneNumber == true)                    
                                begin 
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
                                                    goto LabelSukses
                                                end
                                            endif

                                            label LabelSukses: 
                                                display "Pembayaran sukses"

                                            call proPembayaran
                                        end

                                    else 
                                        begin 
                                            display "Input pin dengan benar"
                                        end
                                    endif
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

                                    numeric nConfirm, nAvg

                                    display nNominal

                                    display "Harap konfirmasi pembayaran"
                                    accept nConfirm

                                    if(nConfirm == true )
                                        begin 
                                            if(nSaldo >= nNominal)
                                                begin 
                                                    compute nAvg as (nNominal - nSaldo)
                                                    display nAvg

                                                    display "pembayran telah berhasil"

                                                    call proPembayaran
                                                end
                                            else 
                                                begin 
                                                    display "Harap isi terlebih dahul usaldo anda"
                                                end
                                            endif
                                        end
                                    else
                                        begin
                                            display "Harap coba lagi"
                                        end
                                    endif
                                end
                            endif
                        end
                    else
                        begin 
                            call proPembayaran
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
    procedure nQrCode
    begin 
        numeric nCamera, nQrID, nBeamID, nWaktu, nTarif, 
        boolean nStatusHelm = false ,nBeamStatus = false

        display "Scan QR Pada Beam"
        accept nCamera, nQrID, nBeamID, nWaktu, nTarif, nBeamStatus
        
        if(nSaldo >= "Rp 20.000")
            begin 
                if (nQrID == nBeamID )
                    begin 
                        <!-- display nBeamStatus, nTarif, nWaktu,  -->

                        // Switch Akhiri atau lanjut
                        switch (nUser)
                            begin 
                                case akhiri: 
                                    numeric nHargaTotal, nHargaBuka = 1.750, nWaktuMenit 
                                    accept nHargaTotal, nHargaBuka, statusHelm, nWaktuMenit
                                    boolean statusHelm = false

                                    display "Silahkan kembalikan helm di tempat"

                                    compute nHargaTotal as ( nHarga * nWaktuMenit + nHargaBuka ) 

                                    if(nSaldo <= nHargaTotal)
                                        begin 
                                            goto saldoKurang
                                        end
                                    else
                                        begin 
                                            goto akhir
                                        end
                                    endif


                                    label saldoKurang : 
                                        numeric nKurangSaldo
                                        accept nKurangSaldo

                                        compute nSaldoKurang as ( nSaldo - nHargaTotal)
                                        
                                        if(nStatusHelm == true)
                                            begin
                                                display "saldo anda kurang, saldo anda akan dipotong saat melakukan top up nanti" 
                                                nSaldo = 0 
                                                call mainPage
                                            end
                                        else 
                                            begin 
                                                numeric nHargaDenda
                                                accept nHargaDenda

                                                compute nDendaKeseluruhan as (nSaldoKurang + nHargaDenda)
                                                

                                                display "saldo anda kurang, saldo anda akan dipotong saat melakukan top up nanti" 
                                                nSaldo = 0 
                                                call mainPage
                                            end
                                        endif

                                        

                                    
                                    label akhir : 

                                        if(nStatusHelm == true)
                                            begin 
                                                compute nTarifAkhir as ( nSaldo - nHargaTotal )
                                                display nTarifAkhir

                                                call mainPage
                                            end
                                        else
                                            begin 
                                                goto dendaHelm
                                            end
                                        endif

                                    label dendaHelm : 
                                        numeric nHargaDendaHelm, nDendaSaldo
                                        accept nHargaDendaHelm, nDendaSaldo
                                        compute nKeselurahanDenda as ( nHargaTotal + nHargaDendaHelm ) 
                                    
                                        if(nSaldo > nKeselurahanDenda)
                                            begin 
                                                compute nPriceEnd as ( nSaldo - nKeselurahanDenda)

                                                display nSaldo // kondisi saldo langsung kepotong meskipun kurang dari harga denda

                                                call mainPage
                                            end
                                        else 
                                            begin 
                                                // Ini Tambah lagi untuk denda nya mulai dari dendaHelm dan saldoKurang 
                                                compute nDendaBayar as (nKeselurahanDenda - nSaldo)
                                                
                                                display "saldo anda kurang, saldo anda akan dipotong saat melakukan top up nanti" 
                                                nSaldo = 0 

                                                call mainPage
                                            end
                                        endif

                                    break

                                default : 
                                    display nBeamStatus, nTarif, nWaktu
                            end // end switch    
                    end // endif begin
                else 
                    begin 
                        display "QR Tidak Cocok "
                    end
                endif // endif nQrCode == nBeamID
            end
        else 
            begin
                display "Saldo harus di atas 20.000 dan Harap isi saldo anda"
                call proPembayaran
            end
        endif // endif nSaldo >= "Rp 20.000"
    end 
```


--- 

### AKUN DAN RIWAYAT
```
    procedure proAccount
    begin 
        character nEmail, nfirstName, nLastName, nOption, nHapusAkun
        accept nEmail, nfirstName, nLastName, nOption, nHapusAkun
    

        switch(nOption)
            begin 
                case cProfile : 
                    
                    label nDisplayProfile: 
                        display "Ini Adalah profile anda"

                    display nfirstName, nLastName,nEmail, nHapusAkun
                    
                    boolean nStatusOptionHapusAkun = true
                    accept nStatusOptionHapusAkun

                    if( nHapusAkun == nStatusOptionHapusAkun )
                        begin 
                            character nOptionAlasan, nInputAlasanLainya = false
                            accept nInputAlasanLainya 
                            
                            // list alasan
                            display "Input alasan anda"

                            accept nOptionAlasan

                            call pageWelcome
                        end
                    else 
                        begin 
                            goto nDisplayProfile 
                        end
                    endif

                    break

                case cRiwayat : 
                    character nTanggal, nPukul, nWaktu, nTotalHarga, nDurasi, nPaymentMethod, nRiwayatDetailButton
                    boolean statusKlik = true
                    accept nTanggal, nPukul, nWaktu, nTotalHarga, nDurasi, statusKlik, nPaymentMethod, nRiwayatDetailButton

                    compute nResi as (nTotalHarga, nPaymentMethod)
                    compute nRiwayat as (nTanggal, nPukul, nWaktu, nTotalHarga, nDurasi) 
                    
                    label nBackRiwayat:
                        display "Riwayat Terakhir anda"

                    display nRiwayatDetailButton

                    while(nRiwayatDetailButton == statusKlik)
                        begin 
                            character nResi, nBack
                            accept nResi

                            label nDetailRiwayat: 
                                display "Ini detail riwayat anda"

                            display "Detail perjalanan"
                            display nRiwayat
                            display nResi

                            if(nResi == statusKlik)
                                begin 
                                    display nResi
                                end
                            elseif (nBack == statusKlik)
                                begin 
                                    goto nBackRiwayat
                                end
                            else 
                                begin 
                                    goto nDetailRiwayat
                                end
                            endif
                        end

                    call proAccount

                    break
                    

                case cLogout : 
                    call pageWelcome
                    break
                
                default: 
                    call proAccount
                
            end
        

    end
```

--- 
