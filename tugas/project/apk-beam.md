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
        character nOption
        accept nOption
        switch(nOption)
            begin 
                case loginGoogle : 
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

    character nGmail = neonjake019@gmail.com , nPassword = Neonjake19

    compute nGmailDatabase as (nGmail, nPassword)

    procedure proLogin_Google
    begin
    
        character nAccountGoogle, nGmail, nGmailDatabase

        label BackInput: 
            display "ERROR : Harap menggunakan account yang terdaftar dengan gmail anda"

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
        elseif(nAccountGoogle != nGmailDatabase)
            begin 
                display "Silahkan pilih akun google untuk melanjutkan ke beam"
                display nAccountGoogle

                if(nAccountGoogle == nGmail)
                    begin 
                        call mainPage

                        //Simpan ke database dan menuju mainPage
                        
                        compute nGmailDatabase as (nAccountGoogle + nPhone)
                        call mainPage
                    end
                else
                    begin 
                        display "Akun ini tidak terdaftar dengan gmail anda"
                    end
                endif
            end
        else
            begin 
                goto BackInput
            end
        endif
    end

```
---
### LOGIN PHONE NUMBER

Psuedocode : 
```
    character nPhoneDatabase, nPhone = 811-5133-959 , nNationPhoneCode = +62

    compute nPhoneDatabase as (nPhone, nNationPhoneCode)

    function login_phone
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
                <!-- GA TAU YANG MANA YANG MAU DI MASUKKIN -->

                if(nNationPhoneCode == "+62") 
                    begin 
                        character nKode
                        accept nVerify
                        compute nVerify as (nKode)

                        display nVerify

                        //Simpan ke database dan menuju mainPage
                        accept nPhoneDatabase
                        
                        // bikin status di sini

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
                display "harap masukkan kode telfon negara dan nomor telfon anda dengan benar"
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

                            label BackPin:
                                display "Internet anda tidak stabil, harap coba lagi"

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
                                            else 
                                                begin 
                                                    goto BackPin
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
