# K-meaning

// the second time i post here.. 26/06/2022 
/* this code is my first code of data mining and it explains k-meaning k-neighbor uzing the C# visual studio 2013 version */ 


using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace DataMining21
{
    public partial class Form1 : Form
    {
        double[] C1Degisken1 = { 4.0, 6.0, 10.0 };
        double[] C1Degisken2 = { 2.0, 4.0, 6.0 };
        double[] C2Degisken1 = { 5.0, 11.0 };
        double[] C2Degisken2 = { 1.0, 8.0 };

        public double medyanHesapla(double[] dizi1, double[] dizi2)
        {

            double[] yeniDizi = new double[5];

            double medyan = 0.0;
            for (int i = 0; i < 3; i++)
            {
                yeniDizi[i] = dizi1[i];
            } //end for
            yeniDizi[3] = dizi2[0];
            yeniDizi[3] = dizi2[1];


            Array.Sort(yeniDizi);
            medyan = yeniDizi[2];
            return medyan;
        }
        public Form1()
        {
            InitializeComponent();
        }


        private void button1_Click(object sender, EventArgs e)
        {
            double medyan1 = medyanHesapla(C1Degisken1, C2Degisken1); //birinci medyani hesapladık
            double medyan1e2 = medyanHesapla(C1Degisken2, C2Degisken1); //birincini tablonun ikinci sütunu
            textBox33.Text = medyan1.ToString() + "-----" + medyan1e2.ToString();

            double[] M1 = { ((C1Degisken1[0] + C1Degisken1[1] + C1Degisken1[2]) / C1Degisken1.Length), ((C1Degisken2[0] + C1Degisken2[1] + C1Degisken2[2]) / C1Degisken2.Length) }; //Burada M1 hesapladık
            double[] M2 = { ((C2Degisken1[0] + C2Degisken1[1]) / C2Degisken1.Length), ((C2Degisken2[0] + C2Degisken2[1]) / C2Degisken2.Length) }; //hesapladık

            textBox1.Text = M1[0].ToString() + " -- " + M1[1].ToString();
            textBox2.Text = M2[0].ToString() + " -- " + M2[1].ToString();


            double e1 = ((C1Degisken1[0] - M1[0]) * (C1Degisken1[0] - M1[0])) + ((C1Degisken2[0] - M1[1]) * (C1Degisken2[0] - M1[1])) +
               ((C1Degisken1[1] - M1[0]) * (C1Degisken1[1] - M1[0])) + ((C1Degisken2[1] - M1[1]) * (C1Degisken2[1] - M1[1])) +
               ((C1Degisken1[2] - M1[0]) * (C1Degisken1[2] - M1[0])) + ((C1Degisken2[2] - M1[1]) * (C1Degisken2[2] - M1[1]));

            double e2 = ((C2Degisken1[0] - M2[0]) * (C2Degisken1[0] - M2[0])) + ((C2Degisken2[0] - M2[1]) * (C2Degisken2[0] - M2[1])) +
                ((C2Degisken1[1] - M2[0]) * (C2Degisken1[1] - M2[0])) + ((C2Degisken2[1] - M2[1]) * (C2Degisken2[1] - M2[1]));
            
            textBox3.Text = e1.ToString();
            textBox4.Text = e2.ToString();

            double E = e1 + e2;

            textBox5.Text = E.ToString();

            ///*****************************


            //tablo 8,19 için bunu haazırladık.
            double[] yC1Degisken1 = { 4.0, 6.0, 5.0 };
            double[] yC1Degisken2 = { 2.0, 4.0, 1.0 };
            double[] yC2Degisken1 = { 10.0, 11.0 };
            double[] yC2Degisken2 = { 6.0, 8.0 };




            //buda tablo 8,19 un yeni halinidoldurduk
            //öklid kuralı
            double[] C1x1 = new double[3];
            double[] C1x2 = new double[3];
            double[] C2x1 = new double[2];
            double[] C2x2 = new double[2];

            for (int i = 0; i < 3; i++)
            {
                C1x1[i] = Math.Sqrt((M1[0] - yC1Degisken1[i]) * (M1[0] - yC1Degisken1[i]) + (M1[1] - yC1Degisken2[i]) * (M1[1] - yC1Degisken2[i]));
                //M1'den Uzaklık C1 Ve M2den Uzanklık c1ler
                C1x2[i] = Math.Sqrt((M2[0] - yC1Degisken1[i]) * (M2[0] - yC1Degisken1[i]) + (M2[1] - yC1Degisken2[i]) * (M2[1] - yC1Degisken2[i]));

                textBox6.Text = C1x1[0].ToString() + " -- " + C1x1[1].ToString();
                textBox7.Text = C1x2[0].ToString() + " -- " + C1x2[1].ToString();
            }
            for (int i = 0; i < 2; i++)
            {

                C2x1[i] = Math.Sqrt((M1[0] - yC2Degisken1[i]) * (M1[0] - yC2Degisken1[i]) + (M1[1] - yC2Degisken2[i]) * (M1[1] - yC2Degisken2[i]));
                //M1'den Uzaklık C1 Ve M2den Uzanklık c1ler
                C2x2[i] = Math.Sqrt((M2[0] - yC2Degisken1[i]) * (M2[0] - yC2Degisken1[i]) + (M2[1] - yC2Degisken2[i]) * (M2[1] - yC2Degisken2[i]));
            }
                textBox8.Text = C1x1[0].ToString();
                textBox9.Text = C1x2[0].ToString();

                textBox10.Text = C1x1[1].ToString();
                textBox11.Text = C1x2[1].ToString();

                textBox12.Text = C1x1[2].ToString();
                textBox13.Text = C1x2[2].ToString();

                textBox14.Text = C2x1[0].ToString();
                textBox15.Text = C2x2[0].ToString();

                textBox16.Text = C2x1[1].ToString();
                textBox17.Text = C2x2[1].ToString();

            double medyan2 = medyanHesapla(C1x1, C2x1); //birinci medyani hesapladık
            double medyan2e2 = medyanHesapla(C1x2, C2x2);
            textBox34.Text = medyan2.ToString() + "-----" + medyan2e2.ToString();

            double[] yM1 = { (yC1Degisken1[0] + yC1Degisken1[1] + yC1Degisken1[2]) / yC1Degisken1.Length, (yC1Degisken2[0] + yC1Degisken2[1] + yC1Degisken2[2]) / yC1Degisken2.Length };

            textBox18.Text = yM1[0].ToString() + "--" + yM1[1].ToString();

            double[] yM2 = { (yC2Degisken1[0] + yC2Degisken1[1]) / yC2Degisken1.Length, (yC2Degisken2[0] + yC2Degisken2[1]) / yC2Degisken2.Length };

            textBox19.Text = yM2[0].ToString() + "-- " + yM2[1].ToString();

            double ye1 = ((yC1Degisken1[0] - yM1[0]) * (yC1Degisken1[0] - yM1[0])) + ((yC1Degisken2[0] - yM1[1]) * (yC1Degisken2[0] - yM1[1])) +
         ((yC1Degisken1[1] - yM1[0]) * (yC1Degisken1[1] - yM1[0])) + ((yC1Degisken2[1] - yM1[1]) * (yC1Degisken2[1] - yM1[1])) +
         ((yC1Degisken1[2] - yM1[0]) * (yC1Degisken1[2] - yM1[0])) + ((yC1Degisken2[2] - yM1[1]) * (yC1Degisken2[2] - yM1[1]));


            //kitapta yanlış yapılmış.

            double ye2 = ((yC2Degisken1[0] - yM2[0]) * (yC2Degisken1[0] - yM2[0])) + ((yC2Degisken2[0] - yM2[1]) * (yC2Degisken2[0] - yM2[1])) +
             ((yC2Degisken1[1] - yM2[0]) * (yC2Degisken1[1] - yM2[0])) + ((yC2Degisken2[1] - yM2[1]) * (yC2Degisken2[1] - yM2[1]));

            textBox20.Text = ye1.ToString();
            // e2 2,50 olması lazım
            textBox21.Text = ye2.ToString();


            double yE = ye1 + ye2;
            textBox22.Text = yE.ToString();
            ////

            //yukarıkadki satır yeni M dir
            double[] yC1x1 = new double[3];
            double[] yC1x2 = new double[3];
            double[] yC2x1 = new double[2];
            double[] yC2x2 = new double[2];
            for (int i = 0; i < 3; i++)
            {

                yC1x1[i] = Math.Sqrt((yM1[0] - yC1Degisken1[i]) * (yM1[0] - yC1Degisken1[i]) + (yM1[1] - yC1Degisken2[i]) * (yM1[1] - yC1Degisken2[i]));
                //M1'den Uzaklık C1 Ve M2den Uzanklık c1ler
                yC1x2[i] = Math.Sqrt((yM2[0] - yC1Degisken1[i]) * (yM2[0] - yC1Degisken1[i]) + (yM2[1] - yC1Degisken2[i]) * (yM2[1] - yC1Degisken2[i]));

            }
            for (int i = 0; i < 2; i++)
            {

                yC2x1[i] = Math.Sqrt((yM1[0] - yC2Degisken1[i]) * (yM1[0] - yC2Degisken1[i]) + (yM1[1] - yC2Degisken2[i]) * (yM1[1] - yC2Degisken2[i]));
                //M1'den Uzaklık C1 Ve M2den Uzanklık c1ler
                yC2x2[i] = Math.Sqrt((yM2[0] - yC2Degisken1[i]) * (yM2[0] - yC2Degisken1[i]) + (yM2[1] - yC2Degisken2[i]) * (yM2[1] - yC2Degisken2[i]));

            }

            textBox23.Text = yC1x1[0].ToString();
            textBox24.Text = yC1x2[0].ToString();

            textBox25.Text = yC1x1[1].ToString();
            textBox26.Text = yC1x2[1].ToString();

            textBox27.Text = yC1x1[2].ToString();
            textBox28.Text = yC1x2[2].ToString();

            textBox29.Text = yC2x1[0].ToString();
            textBox30.Text = yC2x2[0].ToString();

            textBox31.Text = yC2x1[1].ToString();
            textBox32.Text = yC2x2[1].ToString();

            double medyan3 = medyanHesapla(yC1x1, yC2x1); //birinci medyani hesapladık
            double medyan3e2 = medyanHesapla(yC1x2, yC2x2);
            textBox35.Text = medyan3.ToString() + "-----" + medyan3e2.ToString();
        }
    }
}
