VI. Jawaban Pertanyaan Refleksi

1. Apa yang terjadi jika kalian menghapus constructor kosong di Entity Room?
	• Jawaban: Aplikasi akan mengalami error kompilasi (Compile-time error). Room menggunakan constructor kosong (no-argument constructor) untuk melakukan instansiasi objek Entity saat mengambil data hasil query dari database SQLite. Jika dihapus (dan ada constructor berparameter lain), Room tidak akan tahu cara membuat objek tersebut dan memicu error: error: Cannot find a setter for the field / Room cannot find a suitable constructor.

2. Mengapa ViewModel tidak boleh meng-import android.widget.TextView? Hubungkan dengan prinsip Abstraction.
	• Jawaban: Sesuai prinsip Abstraction dan Separation of Concerns (SoC), ViewModel berada di layer Logic/Architecture, sedangkan TextView adalah komponen visual dari Android UI Framework (View Layer). Jika ViewModel meng-import komponen UI, ViewModel menjadi terikat erat (tightly coupled) dengan siklus hidup Activity/Context tertentu. Hal ini melanggar abstraksi, merusak fitur ketahanan rotasi layar karena memicu memory leak, serta menghambat proses pengujian komponen (unit testing) secara independen tanpa emulator.

3. Berikan 1 contoh nyata di studi kasus ini di mana Polymorphism menghemat baris kode kalian.
	• Jawaban: Contoh paling nyata ada pada implementasi PolymorphicListAdapter dan pemanggilan person.getRole() / ((EvaluasiAkademik) person).getStatusAkademik(). Tanpa polimorfisme, kita terpaksa harus membuat 2 Adapter terpisah (MahasiswaAdapter dan DosenAdapter) serta 2 berkas layout view holder yang berbeda. Polimorfisme memungkinkan objek Mahasiswa dan Dosen diperlakukan secara seragam sebagai tipe data komponen Person atau EvaluasiAkademik, sehingga mereduksi baris kode adapter hingga 50%.
