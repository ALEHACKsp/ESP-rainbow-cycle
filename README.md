# ESP-rainbow-cycle

#### Hey guys I was messing around and thought it would be cool to have a rainbow color cycle for ESP. This has definitely been done before but I couldn't find anything on it.

#### Pretty simple but I think it's pretty cool; enjoy! 

#### (The "Wave speed" slider could be changed to make more sense by making it so that the greater the number the faster it goes but I just left it at the sleep duration)



https://user-images.githubusercontent.com/85826349/126025084-3fff7bc3-c622-42cb-9727-51e5f7973de5.mp4

##### Wave Code 


```
#pragma once
 
#include <Windows.h>
 
typedef struct
{
	DWORD R;
	DWORD G;
	DWORD B;
	DWORD A;
}RGBA;
 
RGBA espWave = { 255, 0, 0, 255 };
int wave_speed = 1;
 
void animate() {
	while (true) {
		if (espWave.B != 255 && espWave.G == 0) {
			espWave.B++;
			Sleep(wave_speed);
		}
 
		if (espWave.B == 255 && espWave.R != 0) {
			espWave.R--;
			Sleep(wave_speed);
		}
 
		if (espWave.B == 255 && espWave.G != 255 && espWave.R == 0) {
			espWave.G++;
			Sleep(wave_speed);
		}
 
		if (espWave.G == 255 && espWave.B != 0) {
			espWave.B--;
			Sleep(wave_speed);
		}
 
		if (espWave.B == 0 && espWave.R != 255) {
			espWave.R++;
			Sleep(wave_speed);
		}
		
		if (espWave.R == 255 && espWave.G != 0) {
			espWave.G--;
			Sleep(wave_speed);
		}
	}
}
```


##### Usage Code

```
// drawing
void drawbox(Vector3 ..., Vector3 ..., RGBA* color) {
	ImGui::GetOverlayDrawList()->AddRect(..., ..., ImGui::ColorConvertFloat4ToU32(ImVec4(color->R / 255.0, color->G / 255.0, color->B / 255.0, color->A / 255.0)));
}
 
// Render loop
void render() {
		...
        RGBA ESPColor = { espWave.R ,espWave.G, espWave.B, espWave.A };
      	drawbox(..., ..., &ESPColor);
  }
 
// Menu
void menu() {
	...
        ImGui::Text("Wave speed: "); ImGui::SameLine();
        ImGui::SliderInt("##WAVE", &wave_speed, 0, 10, "%d");
}
 
int main() {
	...
	HANDLE rainbowcycle = CreateThread(nullptr, NULL, (LPTHREAD_START_ROUTINE)animate, nullptr, NULL, nullptr);
	CloseHandle(rainbowcycle);
}
```


***

#### Originally Posted by joaoztz View Post, Mow Is The End Of ColorBots And Is The End Of Cheats Free Why The Cheats Free Is The ColorBots , Now Just Have Cheats Paids And Is 1000$+ I Will Not Buy , Unfortunately This Is Very Sad

***
