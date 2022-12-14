'''
package sb;
import robocode.HitRobotEvent;
import robocode.Robot;
import robocode.ScannedRobotEvent;

import java.awt.*;
//import java.awt.Color;

// API help : https://robocode.sourceforge.io/docs/robocode/robocode/Robot.html

/**
 * FirstBot - a robot by (your name here)
 */
public class FirstBot extends Robot
{
	/**
	 * run: FirstBot's default behavior
	 */
 	boolean peek; 
	double moveAmount; 

	

	 
	public void run() {
		// Set colors
		setBodyColor(Color.black);
		setGunColor(Color.black);
		setRadarColor(Color.orange);
		setBulletColor(Color.cyan);
		setScanColor(Color.cyan);


		moveAmount = Math.max(getBattleFieldWidth(), getBattleFieldHeight());

		peek = false;

		turnLeft(getHeading() % 90);
		ahead(moveAmount);

		peek = true;
		turnGunRight(90);
		turnRight(90);

		while (true) {

			peek = true;

			ahead(moveAmount);

			peek = false;

			turnRight(90);
		}
	}

	


	public void onHitRobot(HitRobotEvent e) {

		if (e.getBearing() > -90 && e.getBearing() < 90) {
			back(100);
		} 
		else {
			ahead(100);
		}
	}




	public void onScannedRobot(ScannedRobotEvent e) {
		fire(2);

		if (peek) {
			scan();
		}
	}
}
'''
