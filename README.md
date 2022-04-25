# WordPress/WooCommerce Kodlar

**Not:** Lütfen dikkatli olun ve yedek alın!

**WORDPRESS TEMA KODLARI**

- [Tema Title Çekme](#tema-title-cekme)

- [Öne Çıkarılmış Görsel Adresi Çekme](#wordpres-on-gorsel-url)

- [Temaya Öne Çıkarılmış Görsel Desteği Ekleme](#wordpres-on-gorsel-destek)


**WORDPRESS HIZLI KODLARI**

- [Son İçerikleri Çekme](#son-icerikler-kodu)

# WORDPRESS TEMA KODLARI

## Tema Title Çekme

```php
/**
 * Wordpress Tema Title Çekme
 */
the_title()
```

## Öne Çıkarılmış Görsel Adresi Çekme

```php
/**
 * Öne Çıkarılmış Görsel Adresi Çekme
 */
echo get_the_post_thumbnail_url($icerik->ID,'medium'); //Seçenekler : thumbnail & full
```

## Öne Çıkarılmış Görsel Adresi Çekme

```php
/**
 * Temaya Öne Çıkarılmış Görsel Desteği Ekleme
 */
add_theme_support( 'post-thumbnails' ); //functions.php eklenecek
```
# WORDPRESS HIZLI KODLARI

## Son İçerikleri Çekme

```php
/**
 * Wordpress Son İçerikleri Çekme
 */
 include 'wp-config.php'; //Anadizindeyse
 $baslangic = 0;
 $limit = 10;
$icerikler = $wpdb->get_results( "SELECT * FROM {$wpdb->prefix}posts WHERE post_status = 'publish' LIMIT $baslangic, $limit" );
foreach($icerikler as $icerik) {
?>
Başlık : <?php echo $icerik->post_title;?><br>
Açıkklama : <?php echo $icerik->post_content;?><br>
Kategoriler : <?php 
$kategoriler = get_the_terms( $icerik->ID, 'category' );
foreach( $kategoriler as $kategori ) {
    echo $kategori->name . ',';
}
?><br>
Resim : <?php echo get_the_post_thumbnail_url($icerik->ID,'medium');?></br>
<?php } ?>
```
