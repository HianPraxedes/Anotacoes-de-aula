# Mergesort (Ordenação intercalada)

- Divisão e conquista

Dado um vetor, divide-o no meio e ordena recursivamente cada metade. Na volta, intercalada as duas metades e obtém o vetor ordenado. Comp.: O(nlgn) (linearítmico)

        void mergeSort (int *v, int e, int d){

            if(d <= e) return;

            int meio = (e+d)/2;

            mergeSort(v, e, meio);
            mergeSort(v, e, meio+1, d);

            intercala(v, e, meio, d);

        }


<div align="center">
	<img src="./fotos/quadro2.jpeg" alt="quadro">
</div>

        Spg = A1(q^n -1)     1(2^(k+1) -1)
            ------------- = --------------- = 2^(k+1) -1
                q-1             2-1