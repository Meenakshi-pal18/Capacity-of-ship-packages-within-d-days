# Capacity-of-ship-packages-within-d-days
class Solution {
public:
bool ship(vector<int>& weights,int mid,int days){
    int actual=1;
    int load=0;
    for(int x:weights){ 
      load+=x;
      if(load>mid){
        actual++;
        load=x;
      }
       
    }
    return actual<=days;
}
    int shipWithinDays(vector<int>& weights, int days) {
        int l = *max_element(weights.begin(), weights.end());
        int r = accumulate(weights.begin(), weights.end(), 0);
        int res=r;
        while(l<=r){
            int mid=l+(r-l)/2;
            if(ship(weights,mid,days)){
                res=mid;
                r=mid-1;
            }
            else{
                l=mid+1;
            }
        }
        return res;
    }
};
