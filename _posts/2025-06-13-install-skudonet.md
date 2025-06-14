---
title: Install Skudonet
author: dzoelfi
date: 2025-06-12 07:00:00 +0700
categories: [Blogging, Skudonet]
tags: [skudonet]
render_with_liquid: false
---

## Intro

Pada tutorial kali ini Penulis akan sharing bagaimana melakukan instalasi Skudonet CE di Debian 12.

Skudonet merupakan load balancer yang disertai dengan fitur WAF atau _Web Application Firewall_, sehingga dapat dipakai juga untuk melindungi website dari berbagai macam serangan / _attack_. Untuk informasi lebih lanjut dapat dicek pada [link berikut](https://www.skudonet.com/)

Laman resmi Skudonet sebenarnya sudah menyediakan file ISO yang dapat digunakan secara langsung untuk di jalankan di _virtual machine_ atau server, namun pada tutorial ini penulis menggunakan metode install _package_ pada Debian Server. 

### Requirement

Sebelum dimulai, ada beberapa hal yang perlu dipersiapkan, diantaranya:

- Server dengan OS Debian 12 (Skudonet hanya support Debian 12)
- Koneksi Internet untuk mengunduh package Skudonet

Setelah keduanya terpenuhi, bisa lanjut ke step instalasi Skudonet.

### Instalasi

Instalasi Skudonet pada Debian 12 cukup mudah dan _straightforward_. Langkah yang perlu dilakukan yaitu menambahkan repository, update repo, dan install Skudonet. Pastikan untuk masuk ke mode root dalam menjalankan perintah berikut. Untuk detail lebih lengkap seperti berikut.

1. Menambah Repositori Skudonet

    > echo "deb http://repo.skudonet.com/ce/v7 bookworm main" >> /etc/apt/sources.list.d/skudonet.list
    ![Desktop View](/assets/img/blog/install-skudonet/cek-repo.png){: .normal }
    > wget -O - http://repo.skudonet.com/ce/skudonet.com.gpg.key | apt-key add -
    ![Desktop View](/assets/img/blog/install-skudonet/add-gpg-key.png){: .normal }
    ![Desktop View](/assets/img/blog/install-skudonet/install-gpg.png){: .normal }

2. Update Repository
   
    > apt update
    ![Desktop View](/assets/img/blog/install-skudonet/update.png){: .normal }

3. Install Skudonet

    > apt install skudonet skudonet-gui-core
    ![Desktop View](/assets/img/blog/install-skudonet/install-skudonet.png){: .normal }

4. Reset password root

    > passwd root
    
    ![Desktop View](/assets/img/blog/install-skudonet/reset-root.png){: .normal }

5. Check Service Skudonet

    > systemctl service skudonet
    ![Desktop View](/assets/img/blog/install-skudonet/skudonet-status.png){: .normal }

6. Akses dashboard Skudonet via Browser
   
   > IP Address:444
   ![Desktop View](/assets/img/blog/install-skudonet/skudonet-login.png){: .normal }


## Hasil
Setelah langkah-langkah sebelumnya sudah dilakukan, Skudonet telah berhasil terinstall dan dapat siap digunakan untuk melindungi website / aplikasi. Untuk masuk ke dashboard Skudonet, masukan user "root" dan "password" yang telah ditentukan sebelumnya.
![Desktop View](/assets/img/blog/install-skudonet/skudonet-dashboard.png){: .normal }\
![Desktop View](/assets/img/blog/install-skudonet/farm.png){: .normal }
![Desktop View](/assets/img/blog/install-skudonet/ssl.png){: .normal }
![Desktop View](/assets/img/blog/install-skudonet/ruleset.png){: .normal }
![Desktop View](/assets/img/blog/install-skudonet/system.png){: .normal }

Demikian tadi tutorial cara menginstall Skudonet di Debian 12. Semoga bermanfaat!

## Referensi

* Install OWASP on Skudonet CE [Link](https://www.skudonet.com/knowledge-base/web-application-firewall-ipds-waf-for-community/installing-owasp-on-skudonet-community-edition-v7/)
* Skudonet Github Repo [Link](https://github.com/SKUDONET/skdlb)