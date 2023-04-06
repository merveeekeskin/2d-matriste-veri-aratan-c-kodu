2 d matirste algoritmanın amacı ve ne için kullanılabileceği ve çalışma şekli:




2 boyutlu bir matriste veri arayan algoritmanın amacı, 


belirli bir koşula uygun olarak, matristeki belirli bir veriyi bulmak veya belirli bir işleme tabi tutmaktır. Matris, satır ve sütunlardan oluşan bir ızgara gibi düzenlenmiş bir veri kümesidir. Bu matrisler genellikle sayılar veya metinler gibi verileri içerir.Veri arama algoritmaları, matrisin her bir elemanını tek tek kontrol ederek belirli bir koşula uygun olan verileri bulur. Bu koşul genellikle bir sayı veya metin ifadesinin aranmasıdır. Algoritma, koşula uygun veriyi bulduğunda, ilgili konum bilgilerini veya verileri çıktı olarak verir.
 Bu algoritma, veri işleme, grafik, yapay zeka, finans ve diğer birçok alanda kullanılabilir. Matrisler, verilerin saklanması, organize edilmesi ve işlenmesi için sıklıkla kullanılır, bu nedenle matris verilerini etkili bir şekilde aramak önemlidir. 
 2 boyutlu bir matriste veri aramak için, genellikle iki yöntem kullanılır: satır satır tarama veya bölünmüş tarama.

Satır satır tarama yöntemi, matrisin her satırını tek tek tarar ve aranan veriyi bulana kadar devam eder. Bu yöntem basit ve kolay uygulanabilir olsa da, büyük matrislerde verimlilik açısından dezavantajları vardır.

Bölünmüş tarama yöntemi ise, matrisi belli parçalara ayırarak arama işlemini gerçekleştirir. Bu yöntemde, matris önce ortadan ikiye bölünür ve aranan veri, bulunan yarı matrislerden birinde mi yoksa diğerinde mi bulunuyor diye kontrol edilir. Bu şekilde, aranılan veri bulunana kadar matris parçaları daha küçük parçalara ayrılır. Bu yöntem, büyük matrislerde daha verimli sonuçlar verir ancak uygulaması daha karmaşıktır.

İki yöntem de temel olarak bir döngü kullanır. Matrisin her bir elemanı, aranan veri ile karşılaştırılır ve eşleşme bulunursa, arama işlemi sonlandırılır. Eşleşme bulunmazsa, döngü devam eder ve matrisin diğer elemanları taranır.





2 d matriste veri arayan ve satır ve sutunları tam sayı değerinde isteyen ve istediği değerleri soldan sağa ve yukarıdan aşağıya doğru sıralandıran c kodu



#include <stdio.h>


// değişkenler tanımlanır


int main() {


    int matris[100][100];
    
    
    int satir, sutun, i, j, k, temp;
    
    
// klavyeden sırayla ilk satır sonra sutun tamsayı değerleri istenir


    printf("Matrisin satir ve sutun boyutlarini giriniz(satir-sutun)(lutfen tamsayi giriniz degerleri): ");
    
    
    scanf("%d %d", &satir, &sutun);
    
    

    printf("Matrisin elemanlarını giriniz:(her elemani girdikten sonra enter tuşuna basiniz) \n");
    
    
    for(i=0; i<satir; i++) {
    
    
        for(j=0; j<sutun; j++) {
        
        
            scanf("%d", &matris[i][j]);
            
            
        }
        
        
    }

    // Her satırdaki elemanları sıralandırılır
    for(i=0; i<satir; i++) {
        for(j=0; j<sutun; j++) {
            for(k=j+1; k<sutun; k++) {
                if(matris[i][j] > matris[i][k]) {
                    temp = matris[i][j];
                    matris[i][j] = matris[i][k];
                    matris[i][k] = temp;
                }
            }
        }
    }

    // Tüm satırları yukarıdan aşağıya sıralandırılır
    for(i=0; i<satir; i++) {
        for(j=i+1; j<satir; j++) {
            int k=0;
            while(matris[i][k] == matris[j][k] && k<sutun) {
                k++;
            }
            if(matris[i][k] > matris[j][k]) {
                for(k=0; k<sutun; k++) {
                    temp = matris[i][k];
                    matris[i][k] = matris[j][k];
                    matris[j][k] = temp;
                }
            }
        }
    }

    // Sıralanmış matrisi yazdır
    printf("Sıralanmış matris: \n");
    for(i=0; i<satir; i++) {
        for(j=0; j<sutun; j++) {
            printf("%d ", matris[i][j]);
        }
        printf("\n");
    }

    return 0;
}







