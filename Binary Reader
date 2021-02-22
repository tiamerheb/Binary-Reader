#include <stdio.h>
#include <stdlib.h>

typedef struct {
        float lat;
        float lon;
        short alt;
        char name[5];
        char misc;
} Track_t;

int main()
{
        FILE *file = fopen("tracks.dat", "rb");
        Track_t track;

        while (fread(&track, sizeof(track), 1, file) != 0) {
                printf("Lat: %.1f", track.lat);
                printf(" lon: %.1f", track.lon);
                printf(" alt: %d", track.alt);
                printf(" name: ");
                for (int i = 0; i < 5; i++) {
                        printf("%c", track.name[i]);
                }
                switch(track.misc & 3){
                        case 0:
                                printf(" ID: unknown");
                                break;
                        case 1:
                                printf(" ID: friend");
                                break;
                        case 2:
                                printf(" ID: foe");
                                break;
                        case 3:
                                printf(" ID: neutral");
                                break;
                }
                switch((track.misc & 12) >> 2){
                        case 0:
                                printf(" Cat: ship");
                                break;
                        case 1:
                                printf(" Cat: ground vehicle");
                                break;
                        case 2:
                                printf(" Cat: airplane");
                                break;
                }
                if(((track.misc & 48) >> 4) == 1){
                        printf(" Engaged");
                }
                printf("\n");
        }

        fclose(file);
        return 0;
}
