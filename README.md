/*# onejavagroup
OneJavaGroup Repo : Java Learning Group 

Project Name: Time Tracking System

Team Name: OneJavaGroup

Team Members: 
        HAgonoy, Ludibeco
	      Echaves, Jeric Melvin
	      Estrada, Jasper
	      Dinawanao, Rickcel Dave
	      Tapales, Kenneth

Project Description: Time Tracking System is a computer application that is capable of logging and saving the data inputted by the user as well as the time and date login and logout.

Date Started: 12/16/2018

Date Expected To Be Realeased: N/A (Not yet discuss with the group)*/





import java.awt.*;
import java.awt.event.ActionListener;
import java.awt.Dimension;
import java.awt.event.*;
import java.io.*;
import javax.swing.*;
import java.text.*;
import java.util.Date;


public class Tts extends JFrame implements ActionListener{
	
	JPanel		panel0, panel1, panel2, panel3, timePanel;
	JTextField	passtf, idNotf;
	JButton		logbtn;
	JLabel     passlbl, idNolbl, timeLabel;
	
	
	Tts(){
		
	logbtn = new JButton("Login");
	logbtn.addActionListener(this);
	
	
	idNolbl = new JLabel("ID No:");
	passlbl = new JLabel("Passcode: ");
	timeLabel = new JLabel();
	
	
	passtf = new JTextField(10);
	idNotf = new JTextField(10);
	
	panel0 = new JPanel();
	panel1 = new JPanel();
	panel2 = new JPanel();
	panel3 = new JPanel();
	timePanel = new JPanel();
	
	final DateFormat timeFormat = new SimpleDateFormat("MMMM/dd/YYYY   HH:mm:ss a");
	ActionListener timerListener = new ActionListener()
        {
            public void actionPerformed(ActionEvent e)
            {
                Date date = new Date();
                String time = timeFormat.format(date);
                timeLabel.setText(time);
            }
        };
        Timer timer = new Timer(1000, timerListener);
        // to make sure it doesn't wait one second at the start
        timer.setInitialDelay(0);
        timer.start();
		
		
	getContentPane().add(timePanel);
	timePanel.setLayout(new BorderLayout(10,10));
	timePanel.add(BorderLayout.CENTER,timeLabel);
	
	getContentPane().add(panel0);
	panel0.setLayout(new BorderLayout(10,10));
	panel0.add(BorderLayout.NORTH, timePanel);
	panel0.add(BorderLayout.WEST,idNolbl);
	panel0.add(BorderLayout.EAST, idNotf);
	
	getContentPane().add(panel1);
	panel1.setLayout(new BorderLayout(10,10));
	panel1.add(BorderLayout.WEST, passlbl);
	panel1.add(BorderLayout.EAST, passtf);
	
	getContentPane().add(panel2);
	panel2.setLayout(new BorderLayout(10,10));
	panel2.add(BorderLayout.NORTH, panel0);
	panel2.add(BorderLayout.CENTER, panel1);
	panel2.add(BorderLayout.SOUTH, logbtn);
	
	
	getContentPane().add(panel3);
	panel3.setLayout(new BorderLayout(10,10));
	panel3.add(BorderLayout.NORTH, panel2);
		
	
		
	}
	
	
	
	public void actionPerformed(ActionEvent event){
		
		String id = idNotf.getText();
		String pass = passtf.getText();
		
		
	}
	
	public static void main(String[] args){
		
	Tts f = new Tts();
	f.setTitle("Time Tracking System");
		
		WindowListener l = new WindowAdapter(){
			
			public void windowClosing(WindowEvent e){
				
				System.exit(0);
				
			}
		};
		f.addWindowListener(l);
		f.pack();
		f.setSize(new Dimension(250,250));
		f.setLocationRelativeTo(null);
		f.setResizable(false);
		f.setVisible(true);
		
	}
	
	
	
	
}
