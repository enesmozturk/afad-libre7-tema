# afad-libre7-tema
 Pardus yüklü PC lerde libre7 için profile ve tema ayarı yapmak için paket kodu


## İçindekiler:
 * Libre7 için office 2013 teması yüklemek
 * Domainde oturum açan her kullanıcı için varsayılan profil ayarlarını yapmak
 
## Adımlar:
### Office 2013 Teması Yükleme
    * /opt/libreoffice7.0/share/config dizini içine temamızı yüklüyoruz.
    * Postint içinde varsayılan tema olan elemantary temasi ile yer değiştiriyoruz.
        **mv /opt/libreoffice7.0/share/config/images_elementary.zip /opt/libreoffice7.0/share/config/images_elementary_2.zip
        **cp /opt/libreoffice7.0/share/config/images_office2013.zip /opt/libreoffice7.0/share/config/images_elementary.zip

### Kulanıcılara Profil Yükleme
    * Yeni kullanıcılar için:
        ** /tmp/afad-libre7-tema altındaki profil dosyasını /etc/skel/.config dizini altına kopyalıyoruz. 
        ** Bu bize yeni kullanıcıların /home/user/.config altına otomatik oluşturmasını sağlayacak
    * Var olan kullanıcılar için (paket yüklemeden önce oluşturulmuş kullanıcılar):
        ```
        ** find /home -type d -name ".config" -exec rm -r "{}"/libreoffice \;
        ** find /home -type d -name ".config" -exec cp -r /etc/skel/.config/libreoffice "{}"/ \;
        ** find /home -type d -name ".config" -exec chmod 777 -R "{}"/libreoffice \;
        ```
        ** Var olan kullanıcıların profil dosyasını silip bizimkisi ile yer değiştirip yetki verdim.

### Libre7 Yazılımı Özelleştirme
    * Açılış ve hakkında kısmına kurumsal logo koyma
        ```
        ** cp -r intro.png /opt/libreoffice7.0/program/
        ** cp -r sofficerc /opt/libreoffice7.0/program/
        ** cp -r shell /opt/libreoffice7.0/program/
        ```
        ** Belirtilen dosyaları kopyalıyoruz.