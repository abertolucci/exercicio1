#include <stdio.h>
#include <stdlib.h>
#include <math.h>
int compare (const void * a, const void * b){
    return ( *(float*)a - *(float*)b );
}

void main(){
    int n, i;
    printf("Digite a quantidade de numeros:\n");
    scanf("%d", &n);
    float *v;
    v = (float*)malloc(sizeof(float) * n);
    printf("Digite os numeros:\n");
    for(i = 0; i < n; i++)
        scanf("%f", &v[i]);
    float min = v[0], max = v[0], dp, media, mediana;
    for(i = 0; i < n; i++){
        if(min > v[i]) min = v[i];
        if(max < v[i]) max = v[i];
    }
    qsort(v, n, sizeof(float), compare);
    if(n&1)
        mediana = v[n/2];
    else
        mediana = (v[n/2-1] + v[n/2]) /2;
    media = 0.0;
    for(i = 0; i < n; i++)
        media += v[i];
    media /= n;
    for(i = 0; i < n; i++)
        dp += (v[i] - media)*(v[i] - media);
    dp = sqrt(dp/(n-1));
    printf("Minimo: %f\n", min);
    printf("Maximo: %f\n", max);
    printf("Media: %f\n", media);
    printf("Mediana: %f\n", mediana);
    printf("Desvio Padrão: %f\n", dp);
    free(v);
}

