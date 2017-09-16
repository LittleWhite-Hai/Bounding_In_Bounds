# Bounding_In_Bounds
a ball is bounding in a window
package bounding_in_plane;

import java.awt.Color;
import java.awt.Graphics;
import java.awt.Graphics2D;
import java.awt.geom.Ellipse2D;

import javax.swing.JComponent;
import javax.swing.JFrame;
import javax.swing.JPanel;

public class MyFrame extends JFrame {

	Ellipse2D.Float r=new Ellipse2D.Float(0F,0F,20F,20F);
	double angle=Math.PI/6;
	float x=0;
	float y=0;
	float t=0;
	
	public static void main(String[] args) {
		MyFrame m=new MyFrame();
		
	}
	public MyFrame() {
		
		setBounds(300,100,500,500);
	
		this.setBackground(new Color(237, 231, 177, 255));
		MyComponent panel =new MyComponent();
		add(panel);
		setDefaultCloseOperation(3);
		//setUndecorated(true);
		setVisible(true);
		getContentPane().setBackground(new Color(255,255,100,255));
		repaint();
		begin();
	}
	private void begin() {
	while(true) {
		x+=Math.cos(angle);
		y+=Math.sin(angle);
		if(x>=this.getWidth()-20) {
			
			t=x-(this.getWidth()-20);
			x=this.getWidth()-20;
			if(t!=0) {
				y-=Math.tan(angle)/t;
				}
		//	r.setFrame(x, y, 20, 20);
			
			angle=Math.PI-angle;
			t=0;
			//System.out.println(1);
		}
		else if(x<=0) {
			t=x;
			x=0;
			if(t!=0) {
				y-=Math.tan(angle)/t;
				}
		//	r.setFrame(x, y, 20, 20);
			angle-=Math.PI;
			angle=Math.PI-angle;
			angle+=Math.PI;
			t=0;
		//	System.out.println(2);
		}
		else if(y>=this.getHeight()-20) {
			t=y-(this.getHeight()-20);
			y=this.getHeight()-20;
			if(t!=0) {
				x-=t/Math.tan(angle);
				}
			//r.setFrame(x, y, 20, 20);
			angle=angle-Math.PI/2;
			angle=Math.PI-angle;
			angle=angle+Math.PI/2;
			t=0;
		//	System.out.println(3);
		}
		else if(y<=0) {
			t=y;
			y=0;
			if(t!=0) {
				x-=t/Math.tan(angle);
				}
			//r.setFrame(x, y, 20, 20);
			angle+=Math.PI/2;
			angle=Math.PI-angle;
			angle-=Math.PI/2;
			t=0;
		//	System.out.println(4);
		}
		r.setFrame(x, y, 20, 20);
		//System.out.println("x="+x+";y="+y);
		try {
			Thread.sleep(10);
		} catch (InterruptedException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
		repaint();
		
	}
	}
	private class MyComponent extends JComponent{
		
		
		public void paint(Graphics g) {
			
			Graphics2D g2=(Graphics2D)g;
			g2.setPaint(new Color(255, 0, 0, 255));
			g2.fill(r);
			g2.draw(r);
		}
	}

}
