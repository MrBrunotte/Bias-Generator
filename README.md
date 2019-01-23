# Bias-Generator
My first program and repository on GitHub. Its a program that generates the bias when daytrading.
I started coding in november 2018 so programming is something completely new to me. My aim is to build a trading software using C#. The software will be based on my trading plan. It will be a trading plan that monitors all my static rules and alerts me when there is an upcoming trade. The Bias generator is the first step and it needs some automation. It is supposed to automatically get the data neccesary to find the current bias according to my rules for bias generation. This first version is a manual generator where the user has to click the boxes.

I'm a daytrader living in Stockholm Sweden and I trade the futures market. I'm a novice programmer that has just embarked on this exciting path of becomming a programmer.

The BIAS GENERATOR
I used the Windos forms app in Visual Basic for this

using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace Bias_Generator
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void Label1_Click(object sender, EventArgs e)
        {

        }

        private void Label1_Click_1(object sender, EventArgs e)
        {

        }

        private void CheckBox1_CheckedChanged_1(object sender, EventArgs e)
        {

        }

        private void Label1_Click_2(object sender, EventArgs e)
        {

        }

        private void CheckBox1_CheckedChanged(object sender, EventArgs e)
        {

        }

        private void ChBHourlyDown_CheckedChanged(object sender, EventArgs e)
        {

        }

        private void lblHourlyColor_Click(object sender, EventArgs e)
        {

        }

        private void Form1_Load(object sender, EventArgs e)
        {

        }

        private void chBLastBarDoji_CheckedChanged(object sender, EventArgs e)
        {

        }

        private void label2_Click(object sender, EventArgs e)
        {

        }

        private void txbInstrument_TextChanged(object sender, EventArgs e)
        {

        }

        private void lblSwingHeader_Click(object sender, EventArgs e)
        {

        }

        private void BtnGoAndGenerateBias_Click(object sender, EventArgs e)     
        {
            // Case 1 BIAS UP: Daily in Rally, Hourly in Rally, No test of SH, Last closed candle is GREEN, no engulfing candle
            if (chbDailyRally.Checked                       // Daily in a rally
                && chbHourlyRally.Checked                   // Hourly in a Rally
                && chbHourlySHNo.Checked                    // No test of hourly SH
                && chbHourlySLNo.Checked                    // No test of hourly SL
                && chbHourlySLAboveNo.Checked               // Close above level - NO
                && chbHourlySLBelowNo.Checked               // Close below level - NO
                && chbLastBarGreen.Checked                  // Last closed bar green
                && chbHourlyTakeOutSHandSLNo.Checked)       // No bar took out both SH and SL
            {
                this.BackColor = Color.Green;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS UP - LOOK FOR LONGS!\n\n" +
                    "Case 1 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is UP\n" +
                    "NO TEST of SH\n" +
                    "Last candle is GREEN\n\n" +
                    "The Bias is UP and we have to look for LONGS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the UP bias until a swing against the UP bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the DOWN swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB entry." +
                    "\n\n if IMPULSIVE and since we have an UP & UP market:" +
                    "\nc) - Look for a delayed PB entry (minimum of 3 signal candles).\n");
                    
            }

            // Case 2 BIAS UP: Daily in Rally, Hourly in Rally, No test of SH, Last closed candle is RED, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Green;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS UP - LOOK FOR LONGS!\n\n" +
                    "Case 2 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is UP\n" +
                    "NO TEST of SH\n" +
                    "Last candle is RED\n\n" +
                    "The Bias is UP and we have to look for LONGS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the UP bias until a swing against the UP bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the DOWN swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB LONG entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB LONG entry." +
                    "\n\n if IMPULSIVE and since we have an UP & UP market:" +
                    "\nc) - Look for a delayed PB LONG entry (minimum of 3 signal candles).\n");
            }

            // Case 3.1 (green candle) BIAS NEUTRAL: Daily in Rally, Hourly in Rally, Test of SH and closed below it, last candle is RED, GREEN or DOJI, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHYes.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 3 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is UP\n" +
                    "TEST of SH and close below SH.\n" +
                    "Last candle color is irrelevant (green)!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" + 
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 3.2 (RED candle) BIAS NEUTRAL: Daily in Rally, Hourly in Rally, Test of SH and closed below it, last candle is RED, GREEN or DOJI, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHYes.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 3 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is UP\n" +
                    "TEST of SH and close below SH.\n" +
                    "Last candle color is irrelevant (red)!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" +
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 3.3 (DOJI candle) BIAS NEUTRAL: Daily in Rally, Hourly in Rally, Test of SH and closed below it, last candle is RED, GREEN or DOJI, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHYes.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarDoji.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 3 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is UP\n" +
                    "TEST of SH and close below SH.\n" +
                    "Last candle color is irrelevant (doji)!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" +
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 4 BIAS is DOWN: Daily in Rally, Hourly in DOWNSWING, No test of SL, Last candle is RED, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Red;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS DOWN - LOOK FOR SHORTS!\n\n" +
                    "Case 4 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "NO TEST of SL\n" +
                    "Last candle is RED or DOJI\n\n" +
                    "The Bias is DOWN and we have to look for SHORTS!\n\n" +
                    "Daily and hourly are in OPPOSITE directions. ONLY trade the DOWN direction of the hourly swing, STOP trading when a GREEN candle closes in the hourly chart!" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the UP swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB SHORT entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB SHORT entry.");
            }

            // Case 4.1 BIAS is DOWN: Daily in Rally, Hourly in DOWNSWING, No test of SL, Last candle is DOJI, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarDoji.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Red;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS DOWN - LOOK FOR SHORTS!\n\n" +
                    "Case 4 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "NO TEST of SL\n" +
                    "Last candle is DOJI or RED\n\n" +
                    "The Bias is DOWN and we have to look for SHORTS!\n\n" +
                    "Daily and hourly are in OPPOSITE directions. ONLY trade the DOWN direction of the hourly swing, STOP trading when a GREEN candle closes in the hourly chart!" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the UP swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB SHORT entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB SHORT entry.");
            }

            // Case 5 (not at SH or SL) BIAS is NEUTRAL: Daily in Rally, Hourly in DOWNSWING, IRRELEVANT where the swing is, Last candle is GREEN, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked                    // irrelevant where the hourly swing is
                    && chbHourlySLNo.Checked                    // irrelevant where the hourly swing is
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)       // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 5 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "IRRELEVANT where the hourly swing is!\n" +
                    "Last candle color is GREEN!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 5.1 (AT SH) BIAS is NEUTRAL: Daily in Rally, Hourly in DOWNSWING, IRRELEVANT where the swing is, Last candle is GREEN, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHYes.Checked                    // irrelevant where the hourly swing is
                    && chbHourlySLNo.Checked                    // irrelevant where the hourly swing is
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)       // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 5 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "IRRELEVANT where the hourly swing is (test of SH and close BELOW)!\n" +
                    "Last candle color is GREEN!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 5.2 (not at SL) BIAS is NEUTRAL: Daily in Rally, Hourly in DOWNSWING, IRRELEVANT where the swing is, Last candle is GREEN, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked                    // irrelevant where the hourly swing is
                    && chbHourlySLYes.Checked                    // irrelevant where the hourly swing is
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)       // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 5 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "IRRELEVANT where the hourly swing is (test of SL and close ABOVE)!\n" +
                    "Last candle color is GREEN!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 6 BIAS is DOWN: Daily DOWN, Hourly DOWN, No test of SL, Last bar RED, no engulfing candle.
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Red;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS DOWN - LOOK FOR SHORTS!\n\n" +
                    "Case 6 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "NO TEST of SL\n" +
                    "Last candle is RED\n\n" +
                    "The Bias is DOWN and we have to look for SHORTS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the DOWN bias until a swing against the DOWN bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the UP swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB SHORT entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB SHORT entry." +
                    "\n\n if IMPULSIVE and since we have an DOWN & DOWN market:" +
                    "\nc) - Look for a delayed PB SHORT entry (minimum of 3 signal candles).\n");
            }

            // Case 7 BIAS is DOWN: Daily DOWN, Hourly DOWN, No test of SL, Last bar GREEN, no engulfing candle.
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Red;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS DOWN - LOOK FOR SHORTS!\n\n" +
                    "Case 7 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "NO TEST of SL\n" +
                    "Last candle is GREEN\n\n" +
                    "The Bias is DOWN and we have to look for SHORTS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the DOWN bias until a swing against the DOWN bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the UP swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB SHORT entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB SHORT entry." +
                    "\n\n if IMPULSIVE and since we have an DOWN & DOWN market:" +
                    "\nc) - Look for a delayed PB SHORT entry (minimum of 3 signal candles).\n");
            }

            // Case 8 (GREEN candle) BIAS is NEUTRAL: Daily in DOWN, Hourly in DOWN, TEST of SL and CLOSE above SL, Last candle is IRRELEVANT, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLYes.Checked                       // Test of SL and close above it!
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked                    // Last candle is green but thats IRRELEVANT!
                    && chbHourlyTakeOutSHandSLNo.Checked)           // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 8 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of HOURLY SL and CLOSE ABOVE the SL!\n" +
                    "Last candle color is IRRELEVANT (green)!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" +
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 8.1 (RED candle) BIAS is NEUTRAL: Daily in DOWN, Hourly in DOWN, TEST of SL and CLOSE above SL, Last candle is IRRELEVANT, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLYes.Checked                       // Test of SL and close above it!
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked                        // Last candle is red but thats IRRELEVANT!
                    && chbHourlyTakeOutSHandSLNo.Checked)           // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 8 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of HOURLY SL and CLOSE ABOVE the SL!\n" +
                    "Last candle color is IRRELEVANT (red)!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" +
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 8.2 (DOJI candle) BIAS is NEUTRAL: Daily in DOWN, Hourly in DOWN, TEST of SL and CLOSE above SL, Last candle is IRRELEVANT, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLYes.Checked                           // Test of SL and close above it!
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarDoji.Checked                         // Last candle is red but thats IRRELEVANT!
                    && chbHourlyTakeOutSHandSLNo.Checked)               // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 8 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of HOURLY SL and CLOSE ABOVE the SL!\n" +
                    "Last candle color is IRRELEVANT (doji)!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" +
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 9 BIAS UP: Daily DOWN, Hourly in RALLY, IRRELEVANT where the hourly swing is, Last closed candle is GREEN, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Green;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS UP - LOOK FOR LONGS!\n\n" +
                    "Case 9 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is UP\n" +
                    "NO TEST of SH\n" +
                    "Last candle is GREEN\n\n" +
                    "The Bias is UP and we have to look for LONGS!\n\n" +
                    "Daily and hourly are in OPPOSITE directions. ONLY trade the UP direction of the hourly swing, STOP trading when a RED candle closes in the hourly chart!" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the DOWN swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB LONG entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB LONG entry.");
            }


            // Case 9.1 BIAS UP: Daily DOWN, Hourly in RALLY, IRRELEVANT where the hourly swing is, Last closed candle is RED, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Green;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS UP - LOOK FOR LONGS!\n\n" +
                    "Case 9 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is UP\n" +
                    "NO TEST of SH\n" +
                    "Last candle is RED\n\n" +
                    "The Bias is UP and we have to look for LONGS!\n\n" +
                    "Daily and hourly are in OPPOSITE directions. ONLY trade the UP direction of the hourly swing, STOP trading when a RED candle closes in the hourly chart!" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the DOWN swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB LONG entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB LONG entry.");
            }

            // Case 10.1 (no test of SH/SL) BIAS is NEUTRAL: Daily in DOWN, Hourly RALLY, IRRELEVANT where the hourly swing is, Last candle is RED, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHYes.Checked
                    && chbHourlySLNo.Checked                       // Test of SL and close above it!
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked                      // Last candle is red but thats IRRELEVANT!
                    && chbHourlyTakeOutSHandSLNo.Checked)           // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 10 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is in a RALLY\n" +
                    "IRRELEVANT where the HOURLY swing is!\n" +
                    "Last candle color is RED!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 10.2 (Test of SH) BIAS is NEUTRAL: Daily in DOWN, Hourly RALLY, IRRELEVANT where the hourly swing is, Last candle is GREEN, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHYes.Checked
                    && chbHourlySLNo.Checked                       // Test of SL and close above it!
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked                      // Last candle is red but thats IRRELEVANT!
                    && chbHourlyTakeOutSHandSLNo.Checked)           // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 10 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is in a RALLY\n" +
                    "IRRELEVANT where the HOURLY swing is!\n" +
                    "Last candle color is GREEN!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 10.3 (Test of SL) BIAS is NEUTRAL: Daily in DOWN, Hourly RALLY, IRRELEVANT where the hourly swing is, Last candle is DOJI, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHYes.Checked
                    && chbHourlySLNo.Checked                       // Test of SL and close above it!
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarDoji.Checked                      // Last candle is red but thats IRRELEVANT!
                    && chbHourlyTakeOutSHandSLNo.Checked)           // No engulfing candle of previous SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 10 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is in a RALLY\n" +
                    "IRRELEVANT where the HOURLY swing is!\n" +
                    "Last candle color is DOJI!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 11 BIAS is NEUTRALIZED
            else if (chbHourlyTakeOutSHandSLYes.Checked)    // if an hourly candle takes out both a SH and SL
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "Previous BIAS IS NEUTRALIZED - STEP ASIDE!\n\n" +
                    "Case 11\n\n" +
                    "The previous BIAS is NEUTRALIZED by the ENGULFING candle!\n\n" +
                    "When a candle takes out a previous SH and SL the previous bias is neutrlized.\n\n" +
                    "- If the next candle breaks beyond the engulfing candle and closes beyond the engulfing candle we have a NEW BIAS\n\n" +
                    "- If it closes within the engulffing candle the bias stays NEUTRAL and we wait for more information!");
            }
            // Case 12 (RED candle) BIAS NEUTRAL: Daily in Rally, Hourly in Down, Test of SL and closed above it, last candle is RED, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLYes.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 12 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SL and close ABOVE SL.\n" +
                    "Last candle color is RED!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 12.1 (DOJI candle) BIAS NEUTRAL: Daily in Rally, Hourly in Down, Test of SL and closed above it, last candle is DOJI, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLYes.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarDoji.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 12 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SL and close ABOVE SL.\n" +
                    "Last candle color is DOJI!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 13 BIAS NEUTRAL (Close above level and red candle): Rally, Rally, Test of SH and close above it, last candle is RED, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySHAboveYes.Checked               // Close above level - YES
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 13 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SH and CLOSE ABOVE SH.\n" +
                    "Last candle color is RED!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" +
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 14 BIAS UP (Close above and green candle): Rally, Rally, Test of SH and close above it, last candle is GREEN, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySHAboveYes.Checked               // Close above level - YES
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Green;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS UP - LOOK FOR LONGS!\n\n" +
                    "Case 14 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is UP\n" +
                    "TEST of SL and CLOSE ABOVE SL.\n" +
                    "Last candle is GREEN\n\n" +
                    "The Bias is UP and we have to look for LONGS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the UP bias until a swing against the UP bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the DOWN swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB LONG entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB LONG entry." +
                    "\n\n if IMPULSIVE and since we have an UP & UP market:" +
                    "\nc) - Look for a delayed PB LONG entry (minimum of 3 signal candles).\n");
            }

            // Case 15 BIAS UP (Close above and doji candle: Rally, Down, Test of SH and close above it, last candle is GREEN, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySHAboveYes.Checked               // Close above level - YES
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarDoji.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Green;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS UP - LOOK FOR LONGS!\n\n" +
                    "Case 15 - UP & UP\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SH and CLOSE ABOVE SH.\n" +
                    "Last candle is DOJI\n\n" +
                    "The Bias is UP and we have to look for LONGS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the UP bias until a swing against the UP bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the DOWN swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB LONG entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB LONG entry." +
                    "\n\n if IMPULSIVE and since we have an UP & UP market:" +
                    "\nc) - Look for a delayed PB LONG entry (minimum of 3 signal candles).\n");
            }

            // Case 16 BIAS NEUTRAL (Close below level and green candle): Down, Down, Test of SL and close below it, last candle is GREEN, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowYes.Checked               // Close below level - YES
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 16 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SL and CLOSE BELOW SL.\n" +
                    "Last candle color is GREEN!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n\n" +
                    "ONLY BOAB SETUPS (NO PB ENTRIES)!\n");
            }

            // Case 17 BIAS DOWN (Close below and RED candle): Down, Down, Test of SL and close below it, last candle is RED, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowYes.Checked               // Close below level - YES
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Red;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS DOWN - LOOK FOR SHORTS!\n\n" +
                    "Case 17 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SL and CLOSE BELOW SL.\n" +
                    "Last candle is RED\n\n" +
                    "The Bias is DOWN and we have to look for SHORTS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the DOWN bias until a swing against the DOWN bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the UP swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB SHORT entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB SHORT entry." +
                    "\n\n if IMPULSIVE and since we have an DOWN & DOWN market:" +
                    "\nc) - Look for a delayed PB SHORT entry (minimum of 3 signal candles).\n");
            }

            // Case 18 BIAS DOWN (Close below and DOJI candle): Down, Down, Test of SL and close below it, last candle is DOJI, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowYes.Checked               // Close below level - YES
                    && chbLastBarDoji.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Red;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS DOWN - LOOK FOR SHORTS!\n\n" +
                    "Case 18 - DOWN & DOWN\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SL and CLOSE BELOW SL.\n" +
                    "Last candle is DOJI\n\n" +
                    "The Bias is DOWN and we have to look for SHORTS!\n\n" +
                    "Daily and hourly are in the same direction, therefore I will stick to the DOWN bias until a swing against the DOWN bias forms (close of the TC in the hourly chart)\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the UP swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB SHORT entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB SHORT entry." +
                    "\n\n if IMPULSIVE and since we have an DOWN & DOWN market:" +
                    "\nc) - Look for a delayed PB SHORT entry (minimum of 3 signal candles).\n");
            }
            // Case 19 BIAS DOWN (Close below and RED candle): RAlly, Down, Test of SL and close below it, last candle is RED, no engulfing candle
            else if (chbDailyRally.Checked
                    && chbHourlyDown.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySLAboveNo.Checked               // Close above level - NO
                    && chbHourlySLBelowYes.Checked               // Close below level - YES
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Red;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS DOWN - LOOK FOR SHORTS!\n\n" +
                    "Case 19 - UP & DOWN\n\n" +
                    "DAILY is UP\n" +
                    "HOURLY is DOWN\n" +
                    "TEST of SL and CLOSE BELOW SL.\n" +
                    "Last candle is RED\n\n" +
                    "The Bias is DOWN and we have to look for SHORTS!\n\n" +
                    "Daily and hourly are in OPPOSITE directions. ONLY trade the DOWN direction of the hourly swing, STOP trading when a GREEN candle closes in the hourly chart!" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the UP swing (againts hourly bias) in the 5min chart!" +
                    "\n\n if CORRECTIVE:" +
                    "\na) - Look for a PB SHORT entry." +
                    "\n\n if IMPULSIVE:" +
                    "\nb) - Look for a BOAB SHORT entry.");
            }
            // Case 20 BIAS UP (Close above and green candle): Down, Rally, Test of SH and close above it, last candle is GREEN, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySHAboveYes.Checked               // Close above level - YES
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarGreen.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.Green;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                    lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS UP - LOOK FOR LONGS!\n\n" +
                    "Case 20 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is UP\n" +
                    "TEST of SH and CLOSE ABOVE SH.\n" +
                    "Last candle is GREEN\n\n" +
                    "The Bias is UP and we have to look for LONGS!\n\n" +
                    "Daily and hourly are in opposite directions, stick to the UP bias until a RED SIGNAL closes in the hourly chart!\n\n" +
                    "\nHOW TO TRADE THIS SCENARIO:\n" +
                    "\n1) Wait for the DOWN swing (againts hourly UP bias) in the 5min chart!" +
                    "\n\n if swing is CORRECTIVE:" +
                    "\na) - Look for a PB LONG entry." +
                    "\n\n if swing is IMPULSIVE:" +
                    "\nb) - Look for a BOAB LONG entry.");
            }
            
            // Case 21 BIAS NEUTRAL (Close above and red candle): Down, Rally, Test of SH and close above it, last candle is RED, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySHAboveYes.Checked               // Close above level - YES
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarRed.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 21 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is UP\n" +
                    "TEST of SH and close ABOVE SH.\n" +
                    "Last candle color is RED!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

            // Case 21.1 BIAS NEUTRAL (Close above and doji candle): Down, Rally, Test of SH and close above it, last candle is DOJI, no engulfing candle
            else if (chbDailyDown.Checked
                    && chbHourlyRally.Checked
                    && chbHourlySHNo.Checked
                    && chbHourlySLNo.Checked
                    && chbHourlySHAboveYes.Checked               // Close above level - YES
                    && chbHourlySLBelowNo.Checked               // Close below level - NO
                    && chbLastBarDoji.Checked
                    && chbHourlyTakeOutSHandSLNo.Checked)
            {
                this.BackColor = Color.LightGray;
                DateTime biasTime = DateTime.Now;
                MessageBox.Show("Current BIAS generated at: \t\t" + biasTime + "\n\n" +
                lblInstrument.Text + "\t " + txbInstrument.Text + "\n\n\n" +
                    "BIAS IS NEUTRAL - STEP ASIDE!\n\n" +
                    "Case 21 - DOWN & UP\n\n" +
                    "DAILY is DOWN\n" +
                    "HOURLY is UP\n" +
                    "TEST of SH and close ABOVE SH.\n" +
                    "Last candle color is DOJI!\n\n" +
                    "The Bias is NEUTRAL and its best to STEP ASIDE for the next hour!\n\n" +
                    "\nONLY TRADE IN THE LAST 30-15 MIN OF THE TRIGGER CANDLE!\n");
            }

        }

        private void btnReset_Click(object sender, EventArgs e) //Reste buttom method
        {
            chbDailyDown.Checked = false;
            chbDailyRally.Checked = false;
            chbLastBarDoji.Checked = false;
            chbHourlyDown.Checked = false;
            chbLastBarGreen.Checked = false;
            chbHourlyRally.Checked = false;
            chbLastBarRed.Checked = false;
            chbHourlySHNo.Checked = false;
            chbHourlySHYes.Checked = false;
            chbHourlySLNo.Checked = false;
            chbHourlySLYes.Checked = false;
            chbHourlyTakeOutSHandSLNo.Checked = false;
            chbHourlyTakeOutSHandSLYes.Checked = false;
            chbHourlySHAboveYes.Checked = false;
            chbHourlySLAboveNo.Checked = false;
            chbHourlySLBelowYes.Checked = false;
            chbHourlySLBelowNo.Checked = false;
            txbInstrument.Text = "";
            this.BackColor = Color.White;
        }
    } } 
 
