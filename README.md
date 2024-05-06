<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400" alt="Laravel Logo"></a></p>

<p align="center">
<a href="https://github.com/laravel/framework/actions"><img src="https://github.com/laravel/framework/workflows/tests/badge.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/dt/laravel/framework" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/v/laravel/framework" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://img.shields.io/packagist/l/laravel/framework" alt="License"></a>
</p>

<b>Requirement/Persyaratan</b>
---
> #### Php versi 8
>> - Cara menginstal php dalam bahasa indonesia : https://youtu.be/Uw3ZGIMvIdA?si=mBVZ-lBnoCilASzo
>> - Cara menginstal php dalam bahasa inggris : https://youtu.be/MPRLUd8Pmyo?si=FqN54nVr4duH4Keg
-----
> #### Laravel versi 10.2.4
>> - cara menginstal laravel yang versi yang sama :
>>   ```
>>   composer create-project laravel/laravel=v10.2.4 belajar-laravel-eloquent
>>   ```
---
<b>Materi/Bahasan</b>
---
> #### apa itu eloquent dalam laravel
> - Eloquent dalam Laravel adalah ORM (Object-Relational Mapping) yang memungkinkan Anda berinteraksi dengan database menggunakan objek-objek PHP. Ini menyediakan cara intuitif dan ekspresif untuk membuat, membaca, memperbarui, dan menghapus data. Anda dapat mendefinisikan model-model Eloquent untuk merepresentasikan tabel-tabel dalam database Anda, mendefinisikan relasi antara model-model tersebut, dan mengeksekusi kueri untuk mengambil data dengan metode chaining yang mudah dipahami. Dengan fitur-fitur seperti mutator, accessor, dan event model, Eloquent membuat pengelolaan data dalam aplikasi Laravel menjadi lebih efisien dan nyaman.
---
> #### Model
> - Model dalam Laravel Eloquent adalah kelas PHP yang merepresentasikan tabel dalam database. Dengan model, Anda dapat melakukan berbagai operasi database seperti membuat, membaca, memperbarui, dan menghapus data.
> -  Model memungkinkan Anda mendefinisikan relasi antar tabel, mengeksekusi kueri dengan mudah, dan menggunakan mutator dan accessor untuk manipulasi data. Anda juga dapat menanggapi peristiwa yang terjadi pada model dengan event model.
> - Keseluruhan, model dalam Eloquent menyediakan antarmuka yang kuat untuk berinteraksi dengan data dalam aplikasi Laravel.
---
> #### Insert
> - Dalam konteks Laravel Eloquent, "insert" merujuk pada operasi untuk menyimpan data baru ke dalam database. Anda dapat menggunakan metode `create()` pada model Eloquent untuk melakukan operasi insert.
> - Contoh sederhana penggunaan `create()` adalah sebagai berikut:
> ```
> use App\Models\User;
>
> // Membuat dan menyimpan record baru dalam database
> $user = User::create([
>    'name' => 'Aldizar Ilham',
>    'email' => 'aldizar@example.com',
>    'password' => bcrypt('password'),
> ]);
> ```
> - Dalam contoh di atas, `create()` akan membuat instance model baru dari kelas `User`, dan menyimpannya ke dalam tabel `users` dalam database. Array yang dilewatkan ke `create()` adalah data yang akan disimpan. Laravel akan secara otomatis mengatur kolom-kolom lain seperti `created_at` dan `updated_at` jika sudah didefinisikan dalam model Anda.
> - Metode `create()` memudahkan Anda untuk menyimpan data baru tanpa perlu menulis kueri SQL secara manual, karena Eloquent akan menangani pembuatan kueri insert untuk Anda di belakang layar.
---
> #### Insert Many
> - Insert many dalam Laravel Eloquent adalah operasi untuk menyimpan banyak baris data ke dalam database sekaligus. Anda dapat menggunakan metode `insert()` pada model Eloquent dan menyediakan array multidimensi yang berisi data yang akan dimasukkan. Setiap elemen dalam array luar mewakili satu baris data, dan setiap elemen dalam array dalam mewakili nilai kolom yang sesuai. Ini lebih efisien daripada menyisipkan satu per satu.
> - Berikut adalah contoh penggunaan `insert()` untuk insert many :
> ```
>  use App\Models\User;
>
> // Data yang akan dimasukkan
> $users = [
>    ['name' => 'Aldizar Ilham', 'email' => 'aldizar@example.com', 'password' => bcrypt('password')],
>    ['name' => 'Lulu Salsabila', 'email' => 'lulu@example.com', 'password' => bcrypt('password')],
>    // Data lainnya
> ];
>
> // Melakukan insert many
> User::insert($users);
> ```
> - Dalam contoh di atas, kita memiliki sebuah array `$users` yang berisi data beberapa pengguna. Kemudian, kita menggunakan metode `insert()` pada model `User` untuk menyisipkan semua data sekaligus ke dalam tabel `users` dalam database.
> - Perlu diingat bahwa ketika menggunakan `insert()`, Eloquent tidak akan memicu event model atau menggunakan fitur seperti timestamps (`created_at` dan `updated_at`). Jadi pastikan data yang dimasukkan memenuhi persyaratan yang dibutuhkan. Juga, pastikan untuk memeriksa keamanan data, terutama jika data berasal dari input pengguna.
---
> #### Find
> - Dalam Laravel Eloquent, "find" adalah metode yang digunakan untuk menemukan satu record dalam tabel database berdasarkan nilai kunci primernya (biasanya bernama "id"). Metode `find()` memungkinkan Anda untuk dengan cepat mengambil record dari database tanpa perlu menulis kueri SQL secara manual.
> - Contoh penggunaan `find()` adalah sebagai berikut:
> ```
> use App\Models\User;
>
> // Menemukan user dengan ID 1
> $user = User::find(1);
>
> // Menampilkan data user
> echo $user->name;
>```
> - Dalam contoh di atas, `User::find(1)` akan mencari record dengan kunci primer (id) 1 dalam tabel `users` dan mengembalikan model Eloquent yang mewakili record tersebut. Anda kemudian dapat mengakses kolom-kolom dalam record tersebut menggunakan properti pada model Eloquent.
> - Jika record dengan kunci primer yang diberikan tidak ditemukan, `find()` akan mengembalikan `null`. Jadi pastikan untuk memeriksa apakah record telah ditemukan sebelum mencoba mengaksesnya.
---
> #### UUID
> - UUID (Universally Unique Identifier) dalam Laravel Eloquent adalah jenis data untuk menyimpan identifikasi unik dalam database. Berbeda dengan kunci primer auto-increment, UUID adalah string global unik yang cocok untuk sistem terdistribusi dan melindungi privasi pengguna. Dalam Laravel, Anda dapat menggunakan UUID sebagai kunci primer dengan mendefinisikannya dalam skema tabel migrasi atau model Eloquent. Ini dapat dilakukan dengan mudah menggunakan paket eksternal seperti `ramsey/uuid.`
---
> #### Timestamps
> - Timestamps dalam konteks Laravel Eloquent merujuk pada dua kolom dalam tabel database, yaitu `created_at` dan `updated_at`, yang secara otomatis diatur dan diperbarui oleh Laravel. Ketika Anda menggunakan timestamps pada sebuah model, Laravel secara otomatis akan memperbarui nilai kolom `created_at` ketika record pertama kali dibuat, dan memperbarui nilai kolom `updated_at` setiap kali record tersebut diperbarui.
> - Fitur timestamps ini sangat berguna untuk melacak kapan record dibuat dan terakhir kali diperbarui dalam database. Ini juga memudahkan Anda dalam menerapkan logika terkait waktu, seperti menyortir berdasarkan waktu pembuatan atau pembaruan, atau menentukan apakah record telah diperbarui sejak waktu tertentu.
> - Secara default, Laravel mengasumsikan bahwa tabel yang memiliki kolom timestamps memiliki struktur seperti ini:
>> - `created_at`: Kolom ini menunjukkan waktu ketika record pertama kali dibuat.
>> - `updated_at`: Kolom ini menunjukkan waktu ketika record terakhir kali diperbarui.
> - Anda dapat mengaktifkan timestamps dengan menambahkan properti `$timestamps` ke dalam model Anda. Secara default, nilai properti ini disetel ke `true`, yang berarti Laravel akan menganggap model tersebut memiliki timestamps. Jika Anda tidak ingin menggunakan timestamps, Anda bisa menetapkan nilainya menjadi `false`.
> - Berikut adalah contoh penggunaan timestamps dalam model Eloquent:
> ```
> namespace App\Models;
>
> use Illuminate\Database\Eloquent\Model;
>
> class User extends Model
> {
>    /**
>     * Indicates if the model should be timestamped.
>     *
>     * @var bool
>     */
>    public $timestamps = true;
>}
> ```
> - Dengan menggunakan timestamps, Laravel secara otomatis akan mengelola nilai `created_at` dan `updated_at` ketika record dibuat atau diperbarui, membebaskan Anda dari pekerjaan manual dalam melacak waktu pembuatan dan pembaruan record.
--- 
> #### Fillable Attributes
> - Fillable attributes dalam Laravel Eloquent adalah atribut-atribut dalam model yang diizinkan untuk diisi secara massal. Ini membantu melindungi aplikasi dari serangan atribut masuk yang tidak diinginkan. Anda dapat menentukan atribut yang dapat diisi massal dengan mendefinisikan properti $fillable dalam model Anda. Dengan demikian, hanya atribut-atribut yang terdaftar dalam $fillable yang akan diperhatikan saat menyimpan data ke database.
---
> #### Soft Delete
> - Soft delete dalam Laravel adalah teknik untuk menghapus data secara "lunak", yang berarti data tetap ada dalam database tetapi ditandai sebagai "dihapus". Dengan menggunakan trait SoftDeletes, Laravel secara otomatis menangani proses soft delete untuk Anda. Data yang dihapus secara lunak dapat dipulihkan jika diperlukan.
---
> #### Query Global Scope
> - Query Global Scope dalam Laravel memungkinkan Anda menambahkan kriteria pencarian secara otomatis ke semua kueri yang dilakukan pada model tertentu.
> - Di sini adalah contoh penggunaannya dengan sintaks:
> ```
> namespace App\Scopes;
>
>use Illuminate\Database\Eloquent\Builder;
>use Illuminate\Database\Eloquent\Model;
>use Illuminate\Database\Eloquent\Scope;
>
>class ActiveScope implements Scope
>{
>    public function apply(Builder $builder, Model $model)
>    {
>        $builder->where('active', true);
>    }
>}
>```
> - Kemudian, mendaftarkan scope ke dalam model:
> ```
>namespace App\Models;
>
>use App\Scopes\ActiveScope;
>use Illuminate\Database\Eloquent\Model;
>
>class User extends Model
>{
>    protected static function boot()
>    {
>        parent::boot();
>
>        static::addGlobalScope(new ActiveScope());
>    }
>}
> ```
> - Dengan mendaftarkan Query Global Scope seperti ini, setiap kali kueri dilakukan pada model `User`, kondisi `where('active', true`) akan otomatis diterapkan, memastikan hanya record yang aktif yang akan dikembalikan.
---
> #### Query Local Scope
> - Query Local Scope dalam Laravel memungkinkan Anda mendefinisikan metode khusus pada model untuk mengeksekusi kueri tertentu dengan kriteria pencarian yang sudah ditentukan.
> - Contoh sintaks sederhana adalah sebagai berikut:
> ```
> namespace App\Models;
>
>use Illuminate\Database\Eloquent\Model;
>
>class User extends Model
>{
>    /**
>     * Scope a query to only include active users.
>     *
>     * @param  \Illuminate\Database\Eloquent\Builder  $query
>     * @return \Illuminate\Database\Eloquent\Builder
>     */
>    public function scopeActive($query)
>    {
>        return $query->where('active', true);
>    }
>}
>```
> - Dalam contoh ini, kita mendefinisikan Query Local Scope bernama `scopeActive()`, yang menambahkan kondisi` where('active', true)` ke dalam kueri. Setelah mendefinisikan Query Local Scope, Anda bisa menggunakannya dalam kueri sebagai berikut:
> ```
> // Menggunakan Query Local Scope
> $activeUsers = User::active()->get();
> ```
> - Dengan menggunakan `scopeActive()`, kita dapat dengan mudah melakukan kueri untuk mengambil semua pengguna yang aktif tanpa perlu menuliskan kondisi `where('active', true)` secara manual setiap kali. Hal ini membuat kode lebih bersih dan lebih mudah dipelihara.
--- 
> #### One to One
> - Dalam Laravel Eloquent, hubungan "One to One" adalah ketika setiap record dalam satu model berhubungan dengan satu record dalam model lainnya. Contohnya, setiap pengguna memiliki satu nomor telepon. Ini didefinisikan dengan `hasOne()` di model yang memiliki record terkait, dan `belongsTo(`) di model yang dimiliki.
> - Berikut adalah contoh sintaks untuk mendefinisikan dan menggunakan hubungan "One to One" dalam Laravel Eloquent:
> ```
> namespace App\Models;
>
>use Illuminate\Database\Eloquent\Model;
>
> class User extends Model
> {
>    /**
>     * Mendapatkan nomor telepon pengguna.
>     */
>    public function phone()
>    {
>        return $this->hasOne(Phone::class);
>    }
>}
>
>class Phone extends Model
>{
>   /**
>     * Mendapatkan pengguna yang memiliki nomor telepon ini.
>     */
>    public function user()
>    {
>        return $this->belongsTo(User::class);
>    }
>}
> ```
> - Dalam contoh ini, model `User` memiliki metode `phone()` yang mendefinisikan hubungan "One to One" menggunakan metode `hasOne()`. Di sisi lain, model Phone memiliki metode `user()` yang mendefinisikan hubungan "One to One" sebaliknya menggunakan metode `belongsTo()`.
> - Setelah mendefinisikan hubungan, Anda dapat mengakses record terkait seperti ini:
> ```
> // Mendapatkan nomor telepon pengguna dengan ID 1
>$user = User::find(1);
>$phone = $user->phone;
>
>// Mendapatkan pengguna yang memiliki nomor telepon dengan ID 1
>$phone = Phone::find(1);
>$user = $phone->user;
> ```
> - Dengan menggunakan hubungan "One to One" ini, Anda dapat dengan mudah mengakses dan memanipulasi data antara dua model yang berhubungan satu sama lain.
