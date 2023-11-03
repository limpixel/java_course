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
    procedure login_Option 
    begin 
        character nOtpion
        accept nOtpion
        
        display "Selamat datang di Beam & Lanjutkan ke login"

        switch (nOtpion)
            begin
                case lanjut : 
                    display "Lanjutkan untuk login "
                    call login_Option
                    break
                default : 
                    
                    display "Bergabunglah sekarang untuk berkeliling kota dengan cara paling seru, terjangkau, dan ramah lingkungan"
            end

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
    // declare procedure nQrCode (Bisa aja salah)
    procedure nQrCode

    procedure mainPage
    begin 
        character nUser 
        numeric nBeamNear, nBeamId, nBeamBattery, nBeamTraveled ,nBeamTrack, nTarif, nHargaBuka
        accept nUser, nBeamNear, nBeamId, nBeamBattery, nBeamTraveled ,nBeamTrack, nTarif, nHargaBuka

        switch (nFitur)
            begin 
                case main : 
                    display nBeamNear

                    <!-- Label (ntar nanyak ) -->
                    label beamNear: 
                        display nBeamNear


                    if(nBeamNear) // Di Klik
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
                    endif
                    
                    break
                
                case Pembayaran : 
                    call proPembayaran
                case QRCode : 
                    call nQrCode
                case Account : 
                    call proAccount
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
                    accept nMethodPayment

                    if(nMethodPayment == "Kartu Kredit")
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
                    else if (nMethodPayment == "Shoope Pay")
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
                        
                    else if (nMethodPayment == "Dana")
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
                    else if (nMethodPayment == "Ovo")
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
                            display "Pilih metode pembayaran yang anda inginkan"
                        end
                    endif
                    
            
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
        numeric nCamera, nQrID, nBeamID, nWaktu, nTarif, nBeamStatus = false

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
                                    numeric statusHelm = true, nHargaTotal, nHargaBuka = 1.750, nWaktuMenit 
                                    accept nHargaTotal, nHargaBuka, statusHelm, nWaktuMenit

                                    display "Silahkan kembalikan helm di tempat"

                                    if(nStatusHelm == true)
                                        begin
                                            goto akhir
                                        end
                                    elseif(nSaldo <= nHargaTotal)
                                        begin 
                                            goto saldoKurang
                                        end
                                    else
                                        begin 
                                            display "apakah kamu yakin sudah mengembalikkan helm?"

                                            if(nStatus == false) // double cross checked
                                                begin
                                                    goto dendaHelm
                                                end
                                            else 
                                                begin 
                                                     goto akhir
                                                end
                                            endif
                                        end
                                    endif

                                    label saldoKurang : 
                                        numeric nKurangSaldo
                                        accept nKurangSaldo

                                        compute nHargaTotalKeseluruhan as (nHargaTotal - nSaldo - nKurangSaldo )
                                        
                                        call mainPage

                                    label dendaHelm : 
                                        numeric nHargaDenda
                                        accept nHargaDenda
                                        compute nHargaTotal as ( nHarga * nWaktuMenit + nHargaBuka + nHargaDenda ) 
                                        
                                        while(nSaldo < nHargaTotal)
                                            begin 
                                                compute nHargaTotal - nSaldo

                                                display nSaldo // kondisi saldo langsung kepotong meskipun kurang dari harga denda

                                                call mainPage
                                            end

                                        call mainPage

                                    label dendaAkhir : 
                                        numeric nHargaDenda
                                        accept nHargaDenda
                                        compute nHargaTotal as ( nHarga * nWaktuMenit + nHargaBuka + nHargaDenda ) 
                                        
                                        while(nSaldo < nHargaTotal)
                                            begin 
                                                compute nHargaTotal - nSaldo

                                                display nSaldo // kondisi saldo langsung kepotong meskipun kurang dari harga denda

                                                call mainPage
                                            end

                                        call mainPage

                                    label akhir : 
                                        compute nHargaTotal as ( nHarga * nWaktuMenit + nHargaBuka ) 

                                        compute nHargaTotal - nSaldo 

                                        call mainPage

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
                display "Harap isi saldo anda"
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
                            display nOptionAlasan

                            if(nInputAlasanLainya == "Lainnya")
                                begin 
                                    display "Massukkan Anda sangat penting. Adakah hal lain yang bisa kami bantu?"
                                end    
                            endif

                            accept nOptionAlasan

                        end
                    else 
                        begin 
                            goto nDisplayProfile 
                        end
                    endif

                case cRiwayat : 
                    character nTanggal, nPukul, nWaktu, nTotalHarga, nDurasi, nPaymentMethod, nRiwayatDetailButton
                    boolean statusKlik = true
                    accept nTanggal, nPukul, nWaktu, nTotalHarga, nDurasi, statusKlik, nPaymentMethod, nRiwayatDetailButton

                    compute nResi as (nTotalHarga, nPaymentMethod)
                    compute nRiwayat as (nTanggal, nPukul, nWaktu, nTotalHarga, nDurasi) 
                    
                    label nBackRiwayat:
                        display "Riwayat Terakhir anda"

                    display nRiwayatDetailButton

                    if(nRiwayatDetailButton == statusKlik)
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
                    else
                        begin 
                        end
                    endif

                case cLogout : 
                    call pageWelcome
            end
        

    end
```

--- 
