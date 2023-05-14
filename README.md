# Laporan Proyek Machine Learning - Ahmad Zein Al Wafi

## Domain Proyek

Pelayanan kesehatan terkadang memiliki harga yang mahal seperti yang terjadi di China [(Wang, Y. *et al.* 2012)](https://www.researchgate.net/profile/Jay-Shen/publication/264818599_Why_healthcare_became_so_expensive_in_China_The_transformation_of_healthcare_financing_during_Chinese_economic_development/links/58332fec08ae138f1c0a9b66/Why-healthcare-became-so-expensive-in-China-The-transformation-of-healthcare-financing-during-Chinese-economic-development.pdf) dan Unites States [(He, X. 2014)](https://bhacjournal.org/index.php/juros/article/view/4549) sehingga hal ini dapat menjadi permasalahan bagi sebagian orang yang tidak bisa menjangkaunya, padahal pelayanan kesehatan yang merupakan kunci untuk mencapai cakupan kesehatan yang universal dengan akses ke layanan perawatan kesehatan esensial yang berkualitas dan terjangkau tercantum pada goals 3 target 3.8 SDGs [(IRIS WHO)](https://apps.who.int/iris/handle/10665/208286). Namun dibalik itu, dalam pesatnya pertukaran informasi data medis atau rekam yang bertumbuh sangat cepat dan terjangkau, menjadikan kecerdasan buatan terlihat menjanjikan untuk menggantikan profesi dokter di masa depan [(Jiang, F. et al. 2017)](https://svn.bmj.com/content/2/4/230.full). Dengan menggunakan data dan memberikan kesempatan belajar pada sistem cerdas, sistem mampu untuk memberikan prediksi penyakit dan rekomendasi perawatan terbaik berdasarkan atribut pasien [(Davenport, T. et al. 2019)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6616181/). Namun tak hanya pada proses pembelajaran, sebagai solusi sistem kecerdasan juga harus memiliki kapabilitas untuk adaptif terhadap perubahan serta evaluasi berkala dalam alur kerjanya untuk meningkatkan kualitasnya dalam menangani kehidupan [(Li, R. et al. 2020)](https://www.nature.com/articles/s41746-020-00318-y) sehingga hal ini dapat meningkatkan manajemen cerdas dan efisiensi yang berkorelasi dengan menurunnya biaya pelayanan kesehatan [(Bohr, A & Memarzadeh, K. 2020)](https://www.sciencedirect.com/science/article/pii/B9780128184387000022). Proyek ini mengakomodasi solusi kecerdasan buatan dalam dunia kesehatan secara sederhana melalui hasil riset singkat, khususnya pada prediksi gangguan hati berdasarkan atribut yang dimiliki pasien.

## Business Understanding

### Problem Statements

Memiliki suatu sistem cerdas yang dapat melakukan prediksi gangguan hati berdasarkan atribut yang dimiliki pasien akan sangat membantu dalam efisiensi proses pelayanan kesehatan. Dengan situasi ini, rumusan masalahnya adalah sebagai berikut

- Dapatkah sistem cerdas yang diajukan memprediksi ganguan hati berdasarkan atribut yang dimiliki pasien?
- Dapatkah *feature selection* membantu meningkatkan performa sistem cerdas dalam metrik akurasi?

### Goals

Untuk menjawab masalah tersebut, disusun tujuan dari proyek ini sebagai berikut.

- Mendapatkan model prediksi gangguan hati berdasarkan atribut yang dimiliki pasien
- Menentukan seberapa signifikan pengaruh dan kebermanfaatan dilakukan *feature selection* performa model

### Solution Statement

Solusi yang diajukan untuk memenuhi goals diatas adalah sebagai berikut.

- Mengajukan empat metode *machine learning* yang dapat digunakan untuk dicari model terbaik sesuai matrik evaluasi akurasi, yaitu: MLP(Multi Layer Perceptron), Random Forest Classifier, Decision Tree Classifier, dan Support Vector Classifier
- Mengajukan tiga metode *feature selection* yang berpotensi untuk memberikan keuntungan pada performa model dan memahami seberapa signifikan pengaruhnya, yaitu *univariate feature selection* dan *model feature selection* berbasis pohon

## Data Understanding

Data yang digunakan dalam proyek ini adalah data [ILPD (*Indian Liver Patient Dataset*)
](https://archive.ics.uci.edu/ml/datasets/ILPD+(Indian+Liver+Patient+Dataset)) dari UCI Machine Learning Repository. Kumpulan data ini berisi 416 catatan pasien hati dan 167 catatan pasien non hati. Kumpulan data dikumpulkan dari timur laut Andhra Pradesh, India. Selector adalah label kelas yang digunakan untuk membagi ke dalam kelompok (pasien gangguan hati atau tidak). Kumpulan data ini berisi 441 catatan pasien pria dan 142 catatan pasien wanita. Data memiliki sepuluh fitur yang dapat dipelajari. Data sudah dilabeli oleh pakar sehingga dapat diverifikasi dan digunakan.

### Variabel

*Indian Liver Patient Dataset* memiliki sepuluh variabel sebagai berikut:
- **Umur** 
Umur yang dimiliki oleh pasien
- **Gender** 
Gender dari pasien
- **TB (Total Bilirubin)** 
Senyawa pigmen berwarna kuning yang merupakan produk katabolisme enzimatik biliverdin oleh biliverdin reduktase. Zat ini terbentuk secara normal dari proses penguraian sel darah merah di dalam tubuh. Zat inilah yang memberikan warna kuning pada tinja dan urine. 
- **DB (Direct Bilirubin)**
Sebelum sampai ke organ hati, bilirubin masih belum saling tergabung alias belum terkonjugasi. Setelah melalui proses dan sampai di hati, bilirubin akan bergabung dengan gula tertentu dan kemudian berubah menjadi bilirubin terkonjugasi atau dikenal sebagai bilirubin direk (direct bilirubin).
- **ALP (Alkphos Alkaline Phosphotase)**
*Alkaline Phosphotase* (Fosfatase Alkali) adalah salah satu enzim hidrolase yang terutama ditemukan pada sebagian besar organ tubuh, terutama dalam jumlah besar di hati, tulang, dan plasenta. Ini adalah enzim dalam aliran darah yang bertugas memindahkan gugus fosfat dan membantu memecah protein dalam tubuh. Organ hati menjadi salah satu sumber utama enzim ini. Alkaline Phosphatase  merupakan enzim hati yang dapat masuk ke saluran empedu. Kandung empedu terletak persis di bawah hati atau lever. Kadar fosfatase alkali dapat meningkat jika ada hambatan pada saluran empedu sehingga kadar ini dapat menjadi tanda gangguan kesehatan.
- **ALT (SGPT Alamine Aminotransferase)**
SGPT (*Serum Glutamic Pyruvic Transaminase*) *Alamine Aminotransferase* (Transaminase Alanina) adalah enzim yang dapat dijumpai di dalam serum darah dan berbagai jaringan tubuh, tetapi sering kali dikaitkan dengan kinerja organ hati. Enzim ini merupakan katalisator pada siklus alanina. Sebagai enzim, SGPT sebagian besar dapat ditemukan di dalam hati. Enzim ini biasanya akan masuk ke aliran darah, apabila ada kerusakan pada hati. Itulah sebabnya, hasil dari pemeriksaan SGPT dapat digunakan untuk mengindikasi adanya gangguan pada hati.
- **AST (SGOT Aspartate Aminotransferase)**
*Aspartate Aminotransferase* (Transaminase Aspartat) adalah enzim golongan transaminase yang sering dikaitkan dengan kinerja organ hati, seperti enzim ALT. Namun, SGOT tidak hanya ada pada organ hati, tetapi juga ditemukan di jantung, otot rangka, dan ginjal. Terdapat dua bentuk AST di dalam tubuh yaitu AST mitokondria dan AST dalam bentu bebas. Kadar SGOT/AST digunakan untuk mengetahui kadar enzim hati yang ada di dalam darah dan dapat digunakan untuk membantu dokter mendiagnosis kerusakan hati atau penyakit hati. Ketika sel-sel hati rusak, SGOT akan bocor ke aliran darah, meningkatkan kadar enzim ini dalam darah.
- **TP (Total Protein)**
Protein total adalah pemeriksaan yang dilakukan untuk mengetahui kadar total protein dalam tubuh seseorang, lebih tepatnya albumin dan globulin. Protein total biasanya akan dicek jika pasien mengalami penurunan berat badan tanpa sebab yang jelas, sering lemas, dan menunjukkan gejala yang mengarah pada gangguan hati dan ginjal. Protein adalah komponen yang memiliki berbagai peranan penting di tubuh dan merupakan bahan dasar pembuat sel dan jaringan. Sementara itu, protein dalam bentuk lebih spesifiknya yaitu albumin dan globulin. Terlalu sedikit atau terlalu banyak protein dalam tubuh sama-sama dapat mengakibatkan masalah kesehatan.
- **(ALB) Albumin**
Albumin adalah salah satu protein yang paling banyak ditemukan dalam darah. Protein ini dilepaskan oleh hati sebagai bagian dari fungsi normalnya. Nah, albumin memiliki berbagai peranan penting, seperti menjaga keseimbangan cairan dalam tubuh. Albumin juga berperan dalam menjaga agar cairan yang terdapat dalam pembuluh darah tidak bocor ke jaringan tubuh sekitar. Jika kadar protein ini rendah maka mungkin saja karena ada gangguan pada organ ginjal atau hati. Selain itu, albumin juga berperan dalam perbaikan jaringan dan membantu pertumbuhan dengan mengangkut hormon dan nutrisi penting ke jaringan disekitarnya. Kadar albumin dalam darah bisa dilihat melalui cek albumin. Jika hasil tes menunjukan jumlah yang tidak normal, hal ini bisa menjadi pertanda masalah.
- **(A/G) Albumin and Globulin Ratio**
Rasio A/G adalah rasio albumin dan globulin, dua protein utama dalam darah manusia. Rasio ini digunakan untuk memantau status gizi, fungsi kekebalan, dan kesehatan secara keseluruhan. Rasio A/G yang tinggi atau rendah utamanya terkait dengan penyakit ginjal dan hati.
- **Status**
Selektor yang telah ditandai oleh pakar untuk menjadi pembeda atau label pada dataset.


### EDA

Dataset tersebut dapat dianalisis mula-mula dengan beberapa eksplorasi dan juga visualisasi.
Ditemukan beberapa insight berikut
- Dataset memiliki berbandingan pasien dengan gangguan hati dan manusia normal yang tidak imbang dengan perbandingan sekitar 4:1 seperti yang terlihat pada gambar 1 berikut
\
![gambar1](https://drive.google.com/uc?export=view&id=1qcy6BhR9_r_pHMcX5GswjIxWXvXhmgrj)
Gambar 1
- Dataset memiliki kecenderungan pada kelas pria dengan gangguan hati yang terlihat dengan confusion matrix seperti pada gambar 2 berikut
\
 ![gambar2](https://drive.google.com/uc?export=view&id=1FzMOXhDaO7GrJZKCP47Hcbm-cpJ38Lya)
Gambar 2
- Umur manusia di dataset terlihat memiliki distribusi asimetris yang mendekati normal dengan skewness: -0.02 namun disayangkan mendapat kurtosis: -0.52 yang terlihat seperti pada gambar 3 berikut
\
![gambar3](https://drive.google.com/uc?export=view&id=1SqiIACtgutxYGWmBTclsF6CHCQ2Eawwr)
Gambar 3
- Berberapa fitur memiliki kemiripan dengan fitur lainnya dilihat dari korelasi yang tinggi terutama pada wilayah fitur SGOT, SGPT, ALP, DB, TB sebagai wilayah sendiri dan TP ALB AG sebagai wilayah sendiri seperti yang terlihat pada gambar berikut
\
![gambar](https://drive.google.com/uc?export=view&id=1035Qc-EvvIu37HxmXDGVi4CZe-4c_JHn)
Gambar 4

## Data Preparation

Terdapat beberapa proses dalam persiapan data sebagai berikut

### Cleaning

Pada tahap ini dilakukan pembersihan pada data-data yang tidak memiliki informasi yang berarti, seperti bernilai null atau kosong. Setelah dilakukan pemeriksaan pada dataset, didapatkan bahwa data memiliki null dengan jumlah yang sangat sedikit, oleh karenanya data ini akan dihilangkan. Hal ini untuk menghindari error saat melakukan proses riset dan pengembangan.

### Feature Engineering

#### Input feature

Agar setiap fitur termanfaatkan dengan baik, maka perlu dilakukan pengolahan fitur sesuai dengan isi datanya. Fitur-fitur yang berupa kategori diubah agar dapat menjadi input numerik pada model.

Dari 10 variabel/fitur, dikelompokkan menjadi 2 tipe, yakni ordinal (8 fitur), dan nominal (2 fitur). Setiap tipe diproses sebagai berikut
- Seluruh fitur diubah menjadi tipe data angka baik integel maupun float
- Fitur nominal diubah menjadi bentuk one-hot, sehingga setiap kelas menjadi fitur tersendiri bernilai 0 atau 1

### Feature Selection

Dengan feature engineering, dihasilkan 9 fitur untuk ditraining. Feature selection memiliki potensi untuk membersihkan *noise* pada data sehingga performa model dapat meningkat, namun feature selection juga memiliki potensi untuk menghilangkan fitur yang sebenarnya penting untuk dipelajari oleh sistem. Sehingga pada proyek ini, diajukan tiga model selection yang dilakukan pada dataset, yaitu ANOVA, *Univariate*, *Model Based*
- **ANOVA**
ANOVA adalah sebuah analisis statistik yang menguji perbedaan rerata antar grup, hal ini bisa diterapkan untuk menolak atau menerima asumsi jika variabel memiliki korelasi. Dua variabel dalam analisis satu jalur dapat dikatakan berkorelasi jika nilai P < 0.05 sehingga feature selection dapat dilakukan dengan menghilangkan variabel yang memiliki nilai P > 0.05
- **Univariate**
Pemilihan fitur univariat bekerja dengan memilih fitur terbaik berdasarkan uji statistik univariat
- **Model Based**
Pemilihan fitur berbasis model menggunakan model yang memiliki koefisien korelasi fitur, dalam kasus ini menggunakan metode pohon

Dalam persaingan ini, *Model Based* mengalami kemenangan dengan meningkatkan performa model namun tidak terlalu signifikan dengan rata-rata matrik akurasi keseluruhan model adalah 75% yang kemudian diikuti ANOVA dengan nilai 74%. Hal ini membuktikan dalam ranah data medis,* feature selection* dapat meningkatkan performa model. 
Metode *machine learning* yang sangat terpengaruh dengan *model selection* ini adalah Decision Tree Classifier dengan variansi sebesar 0.0007 dan yang terkecil adalah Multi Layer Perceptron. Hal ini mungkin karena jaringan syaraf tiruan dapat memberikan bobot yang sangat fleksibel untuk setiap fitur.
## Modeling

Proyek ini mengajukan empat metode *machine learning*, yaitu Random Forest Classifier, Decision Tree Classifier, Support Vector Classifier, dan Multi Layer Perceptron. Proyek ini mengajukan solusi kecerdasan buatan secara sederhana pada layanan kesehatan terkhusus pada gangguan hati, berfokus pada riset bagaimana membangun suatu sistem cerdas pada suatu data kesehatan tertentu, sehingga sistem cerdas yang dirancang belum mampu untuk diimplementasikan dalam studi kasus terkait, baik dalam lingkungan sistetis maupun bebas. Model *machine learning* konvensional dibangun dengan bantuan library scikit learn, sedangkan pada model *deep learning* menggunakan bantuan library scikit learn. Pembelajaran juga menggunakan *grid search* sederhana pada setiap model sesuai koefisien yang akan di tuning. 

- **Random Forest Classifier**
Random Forest Classifier membuat hutan dengan melakukan penggabungan pohon-pohon yang telah dilatih. Karena bentuknya seperti hutan, karakteristik ini dapat membantu untuk mencegah overfitting dan tahan terhadap *noise* data, namun hal tersebut membuat metode ini lama untuk dilatih. Tuning pada metode ini dilakukan menggunakan *grid search* pada koefisien n-estimator yaitu koefisien banyaknya pohon yang boleh dimiliki oleh model.
- **Decision Tree Classifier**
Decision Tree Classifier membuat percabangan yang sangat banyak seperti pohon untuk melakukan klasifikasi, dimana percabangan dibuat berdasarkan pembelajaran yang dilakukan. Metode ini sangat sederhana dan cepat untuk dilatih, namun karena sederhana tersebut kadang kurang dapat memahai fitur yang kompleks. Tuning pada metode ini dilakukan menggunakan *grid search* pada koefisien max_depth yaitu koefisien seberapa dalam cabang yang boleh dimiliki oleh model.
- **Support Vector Classifier**
Support Vector Classifier membuat suatu sistem non-linear pada dimensi tinggi untuk melakukan klasifikasi, dimana data training akan ditransformasikan ke dimensi yang lebih tinggi. Kemampuan Supoort Vector Classifier dalam mencapai dimensi yang lebih tinggi sangat memberikan keuntungan untuk meningkatkan performa model, namun SVC tidak diuntungkan jika menghadapi data yang memiliki *noise* dan data yang terlalu banyak. Tuning pada metode ini dilakukan dengan mengganti macam-macam kernel yang dipakai. Kernel adalah fungsi yang digunakan dalam SVM untuk membantu memecahkan masalah. Kernel menyediakan jalan pintas untuk menghindari perhitungan yang rumit. Hal ini menjadikan model dapat mencapai dimensi yang lebih tinggi bahkan mungkin tidak terhingga dan melakukan perhitungan yang lancar dengan bantuannya.
- **Multi Layer Perceptron**
Multi Layer Perceptron membuat suatu black-box berisi jaringan syaraf tiruan multi-layer yang digunakan untuk klasifikasi. Jaringan syarat tiruan sering dijadikan sebagai model machnine learning karena kemampuannya dalam memodelkan sistem kompleks sehingga seperti "dapat mempejalari apapun", namun hal tersebut menjadikan metode ini sangat haus akan data dan membutuhkan sangat banyak data untuk menjadi metode machine learning yang efektif. Jaringan syaraf tiruan pada proyek ini menggunakan dua layer dengan fungsi optimasi *Stochastic Gradient Descent*(SGD), sebuah metode iteratif untuk mengoptimalkan fungsi objektif dengan sifat kehalusan yang sesuai sebagai perkiraan stokastik dari optimasi penurunan gradien yang menggantikan gradien aktual untuk mempermudah perhitungan dan fungsi kesalahan *Binary CrossEntropy* untuk menghitung skor error yang menjadi pinalti probabilitas berdasarkan jarak dari nilai yang diharapkan. Tuning pada metode ini dilakukan menggunakan grid search pada jumlah neuron masing-masing layer. Neuron adalah unit kecil berbentuk fungsi matematika orde satu yang dibungkus dengan fungsi aktivasi, terlihat tak berdaya namun saat bersama koloninya dapat menciptakan kecerdasan yang mungkin tak pernah dijangkau oleh manusia.


## Evaluation

Metrik yang menjadi nilai keberhasilan model salah satunya adalah akurasi, yaitu presentase berapa banyak prediksi model yang benar terhadap Indian Liver Patient Dataset dibanding seluruh Indian Liver Patient Dataset yang diprediksi. Kemudian untuk parametrik metode feature selection adalah varians, parametrik ini menghitung sebaran akurasi model dalam satu dataset yang telah dilakukan *feature selection* maupun tidak. Hal ini dimungkinkan karena pada proyek ini, satu metode *machine learning* dihadapkan pada empat dataset yang berbeda. Hal ini akan menunjukan bagaimana karakteristik respon suatu metode *machine learning* terhadap perubahan data. Dua metrik ini yaitu akurasi dan variansi akan menjadi evaluasi terhadap model untuk menjadi kajian bagaimana peran, kemampuan serta karakteristik suatu machine learning dalam penerapannya di dunia kesehatan sesuai segala permasalahan yang melatarbelakangi proyek ini.

Sesuai dengan karakteristik setiap metode, Random Forest Classifier dan Support Vector Classifier memenangkan persaingan dengan performa model berdasarkan matrik akurasi yang kebetulan sama yaitu 76% dan 76%. Hal ini dapat disebabkan karena karakteristik metode yang dapat mengatasi fitur kompleks untuk melakukan klasifikasi dengan data yang tidak terlalu dan ini sangat menguntungkan untuk data medis dalam kasus ini terkhusus pada ILPD (Indian Liver Patient Dataset) yang memiliki karakteristik unik pula. Dibandingan dengan Multi Layer Perceptron, mungkin dengan kasus tertentu saat melakukan *deployment* dan *monitoring*, metode ini dapat sangat baik digunakan karena akurasinya yang konsisten menghadapi perubahan fitur.

Karena proyek ini mencoba mengakomodasi kebutuhan dunia kesehatan melalui metode machine learning dengan riset singkat dan sederhana, maka hal yang perlu diperhatikan adalah bagaimana berberapa percobaan yang telah dilakukan berkorelasi terhadap dua parametrik tadi yaitu akurasi dan varians. Dua parameter diasumsikan cukup bagi para pemangku kepentingan untuk membuat keputusan bagaimana kecerdasan buatan akan ditempatkan dalam dunia medis. Akurasi sebagai performa harus memiliki nilai yang tinggi untuk menjaga kehidupan pasien dan varians dapat menjadi penglihatan awal bagaimana model berinteraksi pada data yang berbeda-beda.

Semua model yang telah dikembangkan mampu untuk melakukan prediksi walaupun memang akurasi belum terlalu tinggi, hal tersebut dapat ditingkatkan seiring dengan bertambahnya data. Berberapa model memiliki variansi yang signifikan, untuk model yang seperti itu perlu untuk dilakukan riset lebih lanjut, karena pada proses *deployment* data akan terus terupdate. Dari hasil yang sudah di dapat, kemampuan machine learning tak diragukan lagi dapat menjadi solusi di dunia kesehatan.