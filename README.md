# Word-Embedding
Mainstream word embedding training algorithms implemented by pytorch.
```c++
class Solution {
public:
	double findMedianSortedArrays(vector<int>& nums1, vector<int>& nums2) {
		int n = nums1.size();
		int m = nums2.size();

		if (n > m)  //保证数组1一定最短 //为了加快速度 对长度短的进行二分
		{
			return findMedianSortedArrays(nums2, nums1);
		}
		int LMax1 = 0, LMax2 = 0, RMin1 = 0, RMin2 = 0, c1, c2, lo = 0, hi = n;
		while (lo <= hi) {
			c1 = (hi + lo + 1) / 2;
			c2 = (m + n) / 2 - c1;

			LMax1 = (c1 == 0) ? INT_MIN : nums1[c1 - 1];
			RMin1 = (c1 == n) ? INT_MAX : nums1[c1];
			LMax2 = (c2 == 0) ? INT_MIN : nums2[c2 - 1];
			RMin2 = (c2 == m) ? INT_MAX : nums2[c2];

			if (LMax1 > RMin2)
				hi = c1 - 1;
			else if (LMax2 > RMin1)
				lo = c1 + 1;
			else
				break;
		}
		if ((m + n) % 2)
			return min(RMin1, RMin2);
		else
			return ((int64_t)max(LMax1, LMax2) + (int64_t)min(RMin1, RMin2)) / 2.0;
	}
};


```
