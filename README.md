# Calculatrice 
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
using System.Drawing;

namespace Calculator
{
    class calculatrice : Form

    {
        // Declaration des composants //
        private Label LbVal1, LbVal2, Lboperateur, Lbresultat;
        private TextBox TxVal1, TxVal2, TxResultat;
        private ComboBox cboperateur;
        private Button btcalculer, btfermer, bteffacer;
        

        public calculatrice()
        {
            Text = "Calculatrice";
            Size = new Size(400, 400);

            // Creation des compoants //
            LbVal1 = new Label();
            LbVal1.Text = "Valeur 1";
            LbVal1.AutoSize = true;
            LbVal1.Location = new Point(5, 5);

            TxVal1 = new TextBox();
            TxVal1.Location = new Point(100, 5);

            LbVal2 = new Label();
            LbVal2.Text = "Valeur 2";
            LbVal2.AutoSize = true;
            LbVal2.Location = new Point(5, 30);


            TxVal2 = new TextBox();
            TxVal2.Location = new Point(100, 30);

            Lboperateur = new Label();
            Lboperateur.Text = "Operateur";
            Lboperateur.AutoSize = true;
            Lboperateur.Location = new Point(5, 60);

            cboperateur = new ComboBox();
            cboperateur.Location = new Point(100, 60);

            // Ajout des valeurs dans le combo //
            cboperateur.Items.Add("Selectionner");
            cboperateur.Items.Add("+");
            cboperateur.Items.Add("-"); 
            cboperateur.Items.Add("*");
            cboperateur.Items.Add("/");
            cboperateur.SelectedIndex = 0;
            cboperateur.DropDownStyle = ComboBoxStyle.DropDownList; 


            Lbresultat = new Label();
            Lbresultat.Text = "Resultat";
            Lbresultat.AutoSize = true;
            Lbresultat.Location = new Point(5, 90);

            TxResultat = new TextBox();
            TxResultat.Location = new Point(100, 90);
            TxResultat.Enabled = false;

            btcalculer = new Button();
            btcalculer.Text = "Calculer";
            btcalculer.AutoSize = true;
            btcalculer.Location = new Point(30, 150);
            btcalculer.Click += new EventHandler(calculer_click);

            bteffacer= new Button();
            bteffacer.Text = "Effacer";
            bteffacer.AutoSize = true;
            bteffacer.Location = new Point(120, 150);
            bteffacer.Click += new EventHandler(effacer_click);

            btfermer = new Button();
            btfermer.Text = "Fermer";
            btfermer.AutoSize = true;
            btfermer.Location = new Point(210, 150);
            btfermer.Click += new EventHandler(fermer_click);



            // Ajouter les composants sur la fenetre //
            Controls.Add(LbVal1);
            Controls.Add(LbVal2);
            Controls.Add(Lboperateur);
            Controls.Add(Lbresultat);
            Controls.Add(TxVal1);
            Controls.Add(TxVal2);
            Controls.Add(TxResultat);
            Controls.Add(cboperateur);
            Controls.Add(btcalculer);
            Controls.Add(bteffacer);
            Controls.Add(btfermer);

        }

        private void fermer_click(object sender, EventArgs args)
        {
            Application.Exit();

        }
        private void effacer_click(object sender, EventArgs args)
        {
            TxVal1.Text = "";
            TxVal2.Text = "";
            TxResultat.Text = null;
            cboperateur.SelectedIndex = 0;
        }
        private void calculer_click(object sender, EventArgs args)
        {
            double reste = 0.0;

            switch (cboperateur.SelectedItem.ToString())
            {
                case "+":
                    reste= double.Parse(TxVal1.Text) + double.Parse(TxVal2.Text);
                    TxResultat.Text = reste.ToString();
                    break;

                case "-":
                    reste = double.Parse(TxVal1.Text) - double.Parse(TxVal2.Text);
                    TxResultat.Text = reste.ToString();
                    break;
                case "*":
                    reste = double.Parse(TxVal1.Text) * double.Parse(TxVal2.Text);
                    TxResultat.Text = reste.ToString();
                    break;
                case "/":
                    reste = double.Parse(TxVal1.Text) / double.Parse(TxVal2.Text);
                    TxResultat.Text = reste.ToString();
                    break; 

                default:
                    Console.WriteLine("Mauvais choix");
                    break;

            }   
        }
        static void Main(string[] args)
        {
            calculatrice cal = new calculatrice();
            Application.Run(cal);
        }
    }
}
