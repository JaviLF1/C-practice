#include <Wire.h>
#include <Adafruit_GFX.h>
#include <Adafruit_SSD1306.h>
#define OLED_RESET 4
Adafruit_SSD1306 display(128, 64, &Wire, OLED_RESET);


#define bottonL 12
#define bottonR 11
#define bottonJump 10

int bottonStateR=0;
int bottonStateL=0;
int bottonStateJump=0;

int PlayerCx=0;
int PlayerCy=57;



const unsigned char player [] PROGMEM = {
	0xfe, 0x82, 0x82, 0x82, 0x82, 0x82, 0xfe
};

void setup(){

	pinMode(bottonL, INPUT);
	pinMode(bottonR, INPUT);
	pinMode(bottonJump, INPUT);


	

	display.begin(SSD1306_SWITCHCAPVCC, 0x3C); //or 0x3C
	display.clearDisplay(); //for Clearing the display
  display.drawBitmap(0, 57, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
  display.display();


}


void loop() { 

	bottonStateR=digitalRead(bottonR);
	bottonStateL=digitalRead(bottonL);
	bottonStateJump=digitalRead(bottonJump);

	if (bottonStateR==1){
		
		PlayerCx= PlayerCx + 1;

		display.clearDisplay(); //for Clearing the display
    display.drawBitmap(PlayerCx, 57, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    display.display();


	}

		if (bottonStateL==1){
		
		PlayerCx= PlayerCx -1;

		display.clearDisplay(); //for Clearing the display
    display.drawBitmap(PlayerCx, 57, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    display.display();


	}
		/*
		if (bottonStateJump==1){

			for(int i=0; i<15; i++) {

				PlayerCy= PlayerCy -1;
				

				display.clearDisplay(); //for Clearing the display
    		display.drawBitmap(PlayerCx, PlayerCy, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    		display.display();
				delay(5);

				if (i==14){
					//at is for air time, I used it to gave the efect that it manteins a certain time int the air
					for (int at=0; at<3; at++){
						display.clearDisplay(); //for Clearing the display
    				display.drawBitmap(PlayerCx, PlayerCy, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    				display.display();
						delay(2);
					}


				}



				

			}
			for(int i=0; i<15; i++) {

				PlayerCy= PlayerCy +1;
				

				display.clearDisplay(); //for Clearing the display
    		display.drawBitmap(PlayerCx, PlayerCy, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    		display.display();
				delay(5);
			}*/

		

		if ((bottonStateR==1)&&(bottonStateJump==1)){

			for(int i=0; i<15; i++) {

				PlayerCy= PlayerCy -1;
				PlayerCx= PlayerCx + 1;
				

				display.clearDisplay(); //for Clearing the display
    		display.drawBitmap(PlayerCx, PlayerCy, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    		display.display();
				delay(5);

				if (i==14){
					//at is for air time, I used it to gave the efect that it manteins a certain time int the air
					for (int at=0; at<3; at++){
						display.clearDisplay(); //for Clearing the display
    				display.drawBitmap(PlayerCx, PlayerCy, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    				display.display();
						delay(2);
					}


				}



				

			}
			for(int i=0; i<15; i++) {

				PlayerCy= PlayerCy +1;
				PlayerCx= PlayerCx + 1;
				

				display.clearDisplay(); //for Clearing the display
    		display.drawBitmap(PlayerCx, PlayerCy, player, 7, 7, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    		display.display();
				delay(5);
			}




		}

}

	







 /*for(int i=-32; i<6; i++){

    display.clearDisplay(); //for Clearing the display
    display.drawBitmap(i*16, 0, player, 128, 64, WHITE); // display.drawBitmap(x position, y position, bitmap data, bitmap width, bitmap height, color)
    display.display();


  }*/
	






