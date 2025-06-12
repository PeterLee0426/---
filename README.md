```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(void) {
    int a = 0, n = 0, i, j; // a：勝場次數, n：總場數
    float b;

    srand(time(0)); // 設定亂數種子

    do {
        printf("請輸入你的選擇 1:棒子 2:老虎 3:雞 4:蟲（輸入0結束）：");
        scanf("%d", &i);

        // 若輸入為 0，結束遊戲
        if (i == 0) break;

        // 輸入錯誤處理
        if (i < 1 || i > 4) {
            printf("⚠️ 無效輸入，遊戲結束\n");
            break;
        }

        // 電腦出拳
        j = rand() % 4 + 1;
        switch (j) {
            case 1: printf("電腦：棒子\n"); break;
            case 2: printf("電腦：老虎\n"); break;
            case 3: printf("電腦：雞\n"); break;
            case 4: printf("電腦：蟲\n"); break;
        }

        // 勝負判斷
        if ((i == 1 && j == 2) || // 棒子打老虎
            (i == 2 && j == 3) || // 老虎吃雞
            (i == 3 && j == 4) || // 雞吃蟲
            (i == 4 && j == 1)) { // 蟲咬棒子
            printf("you win\n");
            a++;
        } else if ((j == 1 && i == 2) ||
                   (j == 2 && i == 3) ||
                   (j == 3 && i == 4) ||
                   (j == 4 && i == 1)) {
            printf("you lose\n");
        } else {
            printf("平手\n");
        }

        n++; // 累計總局數

    } while (1);

    // 結算與勝率顯示
    if (n == 0) {
        printf("無有效對戰紀錄，無法計算勝率\n");
    } else {
        b = (float)a / n;
        printf("🎯 獲勝場數：%d\n", a);
        printf("📊 勝率為：%.5f\n", b);
    }

    return 0;
}
```
