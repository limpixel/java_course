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

    begin
       

        // Meminta pengguna untuk memasukkan nomor telepon dan kata sandi
        display "Selamat datang di halaman login."
        repeat
        begin 
            display "Masukkan nomor telepon:"
            accept inputPhoneNumber
            display "Masukkan kata sandi:"
            accept inputPassword
        end until (inputPhoneNumber != "" AND inputPassword != "")

        // Mengecek nomor telepon dan kata sandi dalam array
        
        for(i = 1; i >=5; i + 1)
            if (inputPhoneNumber == phoneNumberArray[i] AND inputPassword == passwordArray[i])
                isLoggedIn = true
                break
            endif
        end

        // Menampilkan hasil login
        if (isLoggedIn)
            display "Login berhasil. Selamat datang!"
        else
            display "Login gagal. Nomor telepon atau kata sandi salah."

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
        numeric nCamera, nQrID, nBeamID, nWaktu, nTarif, nBeamStatus = false

        display "Scan QR Pada Beam"
        accept nCamera, nQrID, nBeamID, nWaktu, nTarif, nBeamStatus
        
        if(nSaldo >= "Rp 20.000")
            begin 
                if (nQrCode == nBeamID )
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
            end
        endif // endif nSaldo >= "Rp 20.000"

    end 
```


--- 

### AKUN DAN RIWAYAT
```
    procedure proSupport
    begin 
        character nEmail, nfirstName, nLastName, nOption
        accept nEmail, nfirstName, nLastName, nOption
    

        switch(nOption)
            begin 
                case cProfile : 
                    display nfirstName, nLastName,nEmail 
                case cRiwayat : 
                case cPanduanBerkendara : 
                case cBeamBisnis : 
                case cLogout : 
            end


    end
```

--- 

### DATABASE PROCEDURE 
```
    procedure nDatabase

    begin     

        // Deklarasi variabel
        character[10] phoneNumberArray[5] // Array nomor telepon
        character[10] passwordArray[5]    // Array password
        character[10] inputPhoneNumber   // Nomor telepon yang dimasukkan pengguna
        character[10] inputPassword      // Kata sandi yang dimasukkan pengguna
        boolean isLoggedIn = false       // Status login

        // Inisialisasi data pengguna
        phoneNumberArray[1] = "1234567890"
        passwordArray[1] = "password1"

        phoneNumberArray[2] = "9876543210"
        passwordArray[2] = "password2"

        phoneNumberArray[3] = "5555555555"
        passwordArray[3] = "password3"

        phoneNumberArray[4] = "1111111111"
        passwordArray[4] = "password4"

        phoneNumberArray[5] = "9999999999"
        passwordArray[5] = "password5"


        for(nDatabase = 0; nDatabase >= 100; nDatabase + 1 )
            begin 
                display phoneNumberArray[]
                display passwordArray[]
                display inputPhoneNumber[]
                display inputPassword[]
            end
        


    end


```