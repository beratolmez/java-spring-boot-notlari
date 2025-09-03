# JavaFX Temelleri: Sahne ve Arayüz Yönetimi

JavaFX, masaüstü uygulamaları geliştirmek için kullanılan bir kütüphanedir. Kullanıcı arayüzü (`UI`) oluşturmada esneklik ve zengin özellikler sunar.

-----

## Sahne (Stage) Yönetimi

Bir JavaFX uygulamasının temelini **Sahne (`Stage`)** ve **Grup (`Group`)** oluşturur.

  * **`Group root = new Group();`**: Uygulamanızdaki tüm arayüz elemanlarının (`UI components`) yer alacağı kök düğümü (`root node`) oluşturur.
  * **`Scene scene = new Scene(root, Color.BLACK);`**: Uygulamanın içeriğini barındıran sahneyi oluşturur. Bu örnekte, sahnenin arka plan rengi siyah olarak ayarlanmıştır.
  * **`stage.setScene(scene);`**: Oluşturulan sahneyi `Stage`'e atar.
  * **`stage.show();`**: Sahneyi kullanıcıya gösterir.
  * **`stage.setTitle("Demo");`**: Uygulamanın pencere başlığını belirler.
  * **`Image icon = new Image("icon.png");`**: Uygulama için bir simge (`icon`) dosyası yükler.
  * **`stage.getIcons().add(icon);`**: Yüklenen simgeyi uygulamanın logosu olarak ayarlar.
  * **`stage.setResizable(false);`**: Kullanıcının pencere boyutunu değiştirmesini engeller.
  * **`stage.setFullScreen(true);`**: Uygulama penceresini tam ekran modunda başlatır.
  * **`stage.setFullScreenExitHint("You can escape with press q");`**: Tam ekrandan nasıl çıkılacağını belirten bir ipucu gösterir.
  * **`stage.setFullScreenExitKeyCombination(KeyCombination.valueOf("q"));`**: Tam ekrandan çıkış için `q` tuşunu kısayol olarak ayarlar.

-----

## CSS ile Stil Ekleme

JavaFX, arayüz elemanlarınıza stil vermek için CSS dosyalarını kullanmanıza olanak tanır.

```java
String css = this.getClass().getResource("application.css").toExternalForm();
scene.getStylesheets().add(css);
```

Bu kod, `application.css` dosyasını bulur ve sahnenin stil sayfalarına ekleyerek arayüz elemanlarının bu stilde görünmesini sağlar.

-----

## Sahne Değiştirme (`Switch Scenes`)

Birden fazla sahne arasında geçiş yapmak, uygulamanın farklı bölümleri için farklı arayüzler oluşturmak gerektiğinde kullanışlıdır.

```java
void switchToScene1(ActionEvent event) throws IOException {
    Parent root = FXMLLoader.load(getClass().getResource("Scene1.fxml"));
    Stage stage = (Stage)((Node)event.getSource()).getScene().getWindow();
    Scene scene = new Scene(root);
    stage.setScene(scene);
    stage.show();
}
```

Bu fonksiyon, tıklanan bir düğmenin (`event.getSource()`) bağlı olduğu sahneye erişir, yeni bir FXML dosyasından (`Scene1.fxml`) yeni bir kök düğüm oluşturur ve bu yeni sahneyi `Stage`'e yükleyerek eski sahnenin yerine geçer.