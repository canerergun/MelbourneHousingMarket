# Melbourne Konut Veri Analizi

Bu belge, Melbourne'daki konut pazarındaki veri analizini gerçekleştirmek için kullanılan adımları içerir. İlk olarak, gerekli kütüphaneler içe aktarılır ve veri kümesi okunur. Daha sonra veri incelenir, eksik değerler belirlenir ve uygun işlemler uygulanır.

## Veri Yükleme ve Temel İnceleme

```python
import pandas as pd

# Veri kümesini okuma
df = pd.read_csv("Melbourne_housing_FULL.csv")

# İlk beş satırı görüntüleme
df.head()

# Sütun isimlerini görüntüleme
df.columns

# Veri çerçevesinin şeklini görüntüleme
df.shape

# Veri tiplerini görüntüleme
df.dtypes

# Eksik değerlerin sayısını hesaplama
df.isnull().sum()
```

## Eksik Değerlerin Görselleştirilmesi

```python
import seaborn as sns

# Seaborn ayarları
sns.set_theme()
sns.set(rc={"figure.dpi":300,"figure.figsize":(12,9)})

# Eksik değerleri görselleştirmek için ısı haritası
sns.heatmap(df.isnull(), cbar=False)
```

## Eksik Değerlerin Doldurulması

```python
# "Price" sütununun ortanca değerini hesaplama
price_median = df["Price"].median()

# Eksik değerleri "Price" sütununun ortanca değeri ile doldurma
df["Price"].fillna(price_median, inplace=True)

# "Price" sütununda hala eksik değer olup olmadığını kontrol etme
df["Price"].isnull().sum()
```

## İstatistiksel Analiz

```python
# "Price" sütununun istatistiksel özeti
df["Price"].describe().round()
```

## Son Kontroller ve Görselleştirmeler

```python
# Yeniden eksik değerleri kontrol etme
df.isnull().sum()

# İlk beş satırı yeniden görüntüleme
df.head()

# Eksik değerleri görselleştirmek için ısı haritası
sns.heatmap(df.isnull(), cbar=False)
```

Bu adımlar, veri setinin incelenmesi, eksik değerlerin belirlenmesi, uygun doldurma stratejilerinin uygulanması ve son olarak veri analizinin yapılmasını içerir.
