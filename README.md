void sort(int tab[N], int low, int high) {
    int mid;

    if(low < high) {
        mid = (low + high) / 2;
        sort(tab, low, mid);
        sort(tab, mid + 1, high);
        merging(tab, low, mid, high);
    } else {
        return;
    }
}

void merging(int tab[N], int start, int mid, int end) {
    int l1, l2, i;
    for(l1 = start, l2 = mid + 1, i = start; l1 <= mid && l2 <= end; i++) {
        if(tab[l1] <= tab[l2])
            tempTab[i] = tab[l1++];
        else
            tempTab[i] = tab[l2++];
    }

    while(l1 <= mid)
        tempTab[i++] = tab[l1++];

    while(l2 <= end)
        tempTab[i++] = tab[l2++];

    for(i = start; i <= end; i++)
        tab[i] = tempTab[i];
}
