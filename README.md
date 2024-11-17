# PerhitunganDiskon
 Tugas 3 - Irfazi - 2210010277

# Deskripsi Program
* Pengguna memasukkan harga asli dan memilih persentase diskon

* Setelah menghitung, tampilkan harga akhir dan jumlah penghematan

# Komponen GUI
JFrame, JPanel, JLabel, JTextField, JComboBox, JButton , JSlider
- JLabel untuk judul aplikasi, seperti "Aplikasi Perhitungan Diskon".
- JLabel untuk label "Harga Asli", JTextField untuk input harga asli (beri nama txtHargaAsli).
- JLabel untuk label "Persentase Diskon", JComboBox (beri nama comboDiskon) untuk pilihan persentase diskon (10%, 20%, 30%, dst.).
- JButton dengan teks "Hitung" dan nama btnHitung.
- JLabel untuk label "Harga Akhir" dan JTextField (beri nama txtHargaAkhir) untuk menampilkan hasil harga akhir (set Editable menjadi false).
- JLabel untuk label "Penghematan" dan JTextField (beri nama txtPenghematan) untuk menampilkan jumlah penghematan (set Editable menjadi false).
- JSlider juga untuk untuk pilihan persentase diskon dan hasil persentase akan tampil di JLabel lblDiskonSlider

# Logika Program
Perhitungan aritmatika, Penanganan eksepsi

# Events
* ActionListener untuk tombol Hitung
 
 private void btnHitungActionPerformed(java.awt.event.ActionEvent evt) {                                          
        try {

            if (fieldAsli.getText().isEmpty() || fieldAsli.getText().equals("Rp ")) {
                JOptionPane.showMessageDialog(this, "Silakan masukkan harga asli.", "Error", JOptionPane.ERROR_MESSAGE);
                return;
            }

            double hargaAsli = Double.parseDouble(fieldAsli.getText().replace("Rp ", ""));

            int diskonPersen;
            if (SdDiskon.getValue() > 0) {
                diskonPersen = SdDiskon.getValue();
            } else {
                String diskonStr = (String) cbxDiskon.getSelectedItem();
                diskonPersen = Integer.parseInt(diskonStr.replace("%", ""));
            }

            String kodeKupon = TextVocer.getText().trim();

            if (kodeKupon.equalsIgnoreCase("ALLITEM50%")) {
                diskonPersen += 10;
            } else if (!kodeKupon.isEmpty()) {
                JOptionPane.showMessageDialog(this, "Kode kupon tidak valid.", "Info", JOptionPane.INFORMATION_MESSAGE);
            }

            // Hitung penghematan dan harga akhir
            double penghematan = hargaAsli * diskonPersen / 100;
            double hargaAkhir = hargaAsli - penghematan;

            // Tampilkan hasil pada JTextField dengan prefix "Rp "
            menghemat.setText("Rp " + String.format("%.2f", penghematan));
            setelahDiskon.setText("Rp " + String.format("%.2f", hargaAkhir));

            // Tambahkan hasil ke riwayat
            String hasilRiwayat = "Harga Asli: Rp " + hargaAsli
                    + ", Diskon: " + diskonPersen + "%"
                    + ", Penghematan: Rp " + String.format("%.2f", penghematan)
                    + ", Harga Akhir: Rp " + String.format("%.2f", hargaAkhir) + "\n";
            riwayatPerhitungan.append(hasilRiwayat);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan nilai yang valid.", "Error", JOptionPane.ERROR_MESSAGE);
        }
    }                                         

            
* ItemListener pada JComboBox untuk memilih persentase diskon

public PerhitunganDiskon() {
        initComponents();
        cbxDiskon.addItem("10%");
        cbxDiskon.addItem("20%");
        cbxDiskon.addItem("30%");
        cbxDiskon.addItem("40%");
        cbxDiskon.addItem("50%");
    }


# Variasi
* Tambahkan opsi untuk memasukkan kode kupon diskon tambahan
  
            String kodeKupon = TextVocer.getText().trim();
            if (kodeKupon.equalsIgnoreCase("ALLITEM50%")) {
                diskonPersen += 10;
            } else if (!kodeKupon.isEmpty()) {
                JOptionPane.showMessageDialog(this, "Kode kupon tidak valid.", "Info", JOptionPane.INFORMATION_MESSAGE);
            }

* Tambahkan JSlider sebagai alternatif JComboBox untuk memilih persentase diskon

           int diskonPersen;
            if (SdDiskon.getValue() > 0) {
                diskonPersen = SdDiskon.getValue();
            } else {
                String diskonStr = (String) cbxDiskon.getSelectedItem();
                diskonPersen = Integer.parseInt(diskonStr.replace("%", ""));
            }

* Sediakan riwayat perhitungan diskon yang telah dilakukan.

 menghemat.setText("Rp " + String.format("%.2f", penghematan));
            setelahDiskon.setText("Rp " + String.format("%.2f", hargaAkhir));

            // Tambahkan hasil ke riwayat
            String hasilRiwayat = "Harga Asli: Rp " + hargaAsli
                    + ", Diskon: " + diskonPersen + "%"
                    + ", Penghematan: Rp " + String.format("%.2f", penghematan)
                    + ", Harga Akhir: Rp " + String.format("%.2f", hargaAkhir) + "\n";
            riwayatPerhitungan.append(hasilRiwayat);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan nilai yang valid.", "Error", JOptionPane.ERROR_MESSAGE);
        }
    } 

## Contoh Gambar Project Setelah di Run
![]()

## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    20    |
|  2  | Logika Program   |    20    |
|  3  | Kesesuaian UI    |    15    |
|  4  | Constructor      |    15    |
|  5  | Memenuhi Variasi |    30    |
|     | TOTAL        | 100 |
