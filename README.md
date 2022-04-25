# WordPress/WooCommerce Kodlar

**Not:** Lütfen dikkatli olun ve yedek alın!


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
 * Temaya Öne Çıkarılmış Görsel Desteği Ekleme */
add_theme_support( 'post-thumbnails' ); //functions.php eklenecek
```

## Tema Menü Desteği Ekleme

```php
/*
Tema Menü Desteği Ekleme
https://developer.wordpress.org/reference/functions/wp_nav_menu/ Daha Fazla
 */

//backend
function menu_bagla() {
    register_nav_menus(
      array(
        'ust-menu' => __( 'Üst Menü' ),
        'yan-menu' => __( 'Yan Menü' ),
        'alt-menu' => __( 'Alt Menü' )
      )
    );
  }
add_action( 'init', 'menu_bagla' );

//frontend
wp_nav_menu( array(
    'menu' => 'Üst Menü'
) );

```


# WORDPRESS HIZLI KODLAR

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

