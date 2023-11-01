<div id="header" width="30%" align="center">
    <img src="../../asset/sip.png" width="30%%" />
    <p>Psuedocode Aplikais Beam</p>
</div>


---
### Welcome Page
---

Psuedocode
```
    procedure login_Option 
    begin 
        character nOtpion
        accept nOtpion
        
        display "Selamat datang di Beam"

        switch (nOtpion)
            begin
                case lanjut : 
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
        numeric nOption
        accept nOption
        switch(nOption)
            begin 
                case login : 
                    call proLogin_Google
                    break
                case numberPhone : 
                    call prooLogin_Phone   
                    break
                default : 
                    display "Pilih Opsi Login yang ingin digunakan"
                    
            end
    end
```
---
### LOGIN GOOGLE ACOUNT
```
    procedure proLogin_Google
    begin
    
        character nAccountGoogle, nGmail, nGmailDatabase

        display "Silahkan pilih akun google untuk melanjutkan ke beam"
        accept nAccountGoogle, nGmail, nGmailDatabase
        display nAccountGoogle

        if(nAccountGoogle == nGmailDatabase )
            begin
                if(nAccountGoogle == nGmail)
                    begin 
                        call mainPage
                    end
                else
                    begin 
                        display "Akun ini tidak terdaftar "
                    end
                endif
            end
        else 
            begin 
                display "Silahkan pilih akun google untuk melanjutkan ke beam"
                display nAccountGoogle

                if(nAccountGoogle == nGmail)
                    begin 
                        call mainPage

                        //Simpan ke database dan menuju mainPage
                        
                        compute nGmailDatabase as (nNationPhoneCode + nPhone)
                        call mainPage
                    end
                else
                    begin 
                        display "Akun ini tidak terdaftar dengan gmail anda"
                    end
                endif
            end
        end
    end

```
---
### LOGIN PHONE NUMBER

Psuedocode : 
```
    function login_phone
    begin 
        character nDatabase, nPhone, nVerify, nNationPhoneCode, 
        
        label Error : 
            display "Harap periksa nomor anda kembali"

        display "Masukkan Kode No.Telpon anda gunakan "
        accept nNationPhoneCode

        display "contoh no.telfon : 81xx-xxx-xxx"
        accept nPhone

        // Di sini ada 2 kondisi dimana pada saat nPhone tidak ada, maka langsung terdaftar
        if(nPhone == nDatabase)
            begin 
                if(nNationPhoneCode == "+62") 
                    begin 
                        character nKode
                        compute nVerify as (nKode)

                        display nVerify

                        //Simpan ke database dan menuju mainPage
                        accept nDatabase
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
                if(nPhone == nNationPhoneCode)
                    begin 
                        character nKode
                        compute nVerify as (nKode)

                        display nVerify

                        //Simpan ke database dan menuju mainPage
                        accept nDatabase
                        compute nDatabase as (nNationPhoneCode + nPhone)
                        call mainPage
                    end
                else 
                    begin 
                        goto Error
                    end
                endif
            end
        endif
    end
```



---
### MAIN PAGE

```
    // declare procedure nQrCode (Bisa aja salah)
    procedure nQrCode

    // declare procedure proSupport (Bisa aja salah)
    procedure proSupport

    procedure mainPage
    begin 
        numeric nUser ,nBeamNear, nBeamId, nBeamBattery, nBeamTraveled ,nBeamTrack, nTarif, nHargaBuka
        accept nBeamNear, nBeamId, nBeamBattery, nBeamTraveled ,nBeamTrack, nTarif, nHargaBuka

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
                case Support : 
                    call proSupport
                case Account : 
                    call proAccount
            end


    end
```

### Top Up Saldo 
```
    // producer input kartu kredit atau debit
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
                                            display "Proses pembayaran akan sebentar lagi"
                                            
                                            if(nNetwork == "not stable")
                                                begin 
                                                    display "Internet terlalu rendah, harap mencoba ulang"
                                                end
                                            endif

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
                            numeric nApkOvo, nPopuP, nPin, nSaldoOvo

                            accept nApkOvo, nPopuP, nPin, nSaldoOvo

                            display "Kami akan mengirimkan pop up untuk konfirmasi pembayaran"

                            display nPopUp

                            if(nPopUp == CLICK) // ketika user klik pop upnya
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
        numeric nCamera, nQrID, nBeamID

        display "Scan QR Pada Beam"
        accept nCamera, nQrID, nBeamID

        if(nQrID == nBeamID)
            begin 
                display nQrCode
                
                if(nSaldo >= "Rp 20.000")
                    if (nQrCode == nBeam )
                        display nHarga, nBeamStatus, nTarif 
                        
                        switch (nHarga, nBeamStatus, nTarif )
                            begin 
                                case qrCode :
                                    if(nBeam == nQrCode) 
                                        begin 
                                            display nTarif, nWaktu, 

                                            switch (nUser)
                                                begin 
                                                    case akhiri: 
                                                        numeric statusHelm = true, nHargaTotal, nHargaBuka = 1.750, nWaktuMenit = 60
                                                        accept nHargaTotal, nHargaBuka, statusHelm, nWaktuMenit

                                                        display "Silahkan kembalikan helm di tempat"

                                                        if(nStatusHelm == true)
                                                            begin
                                                                goto akhir
                                                            end
                                                        else
                                                            begin 
                                                                display "apakah kamu sudah mengembalikkan helm?"

                                                                if(nStatus == true)
                                                                    begin
                                                                        goto akhir
                                                                    end
                                                                endif
                                                            end
                                                        endif

                                                        break

                                                    label akhir : 
                                                        compute nHargaTotal as ( nHargaBuka * nWaktuMenit + nHarga ) 

                                                        compute nHargaTotal - nSaldo 

                                                        call mainPage

                                                        break
                                                    default : 
                                                        display nHarga, nBeamStatus, nTarif, nWaktu
                                                        
                                                end
                                        end
                                    endif

                                    break

                                case dering :
                                     display "beam anda berbunyi Saya di sini" 
                                     break
                                default : 
                                    display nBeamNear
                            end
                            
                        

                    else 
                        display "QR Tidak Cocok "
                    endif
                else 
                    display "Harap isi saldo anda"
                endif
            end
        
        else 
            begin 
                display "Beam ID tidak terdaftar"
            end

        endif

    end 
```


--- 

### AKUN DAN RIWAYAT
```
    procedure proSupport
    begin 
        character nEmail, nfirstName, nLastName
        accept nEmail, nfirstName, nLastName

    end
```
