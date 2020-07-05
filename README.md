# cocoevalbyclass

Print AP and AR by class, by modification in cocoeval.py

in line 458 of cocoeval.py, the following code is added to print AP and AR for each class.

```python
				# cacluate AP(average precision) and AR(average recall) for each category
                num_classes = 8 # your class number here. if you have 80 classes, num_classes should be 81
                avg_ap = 0.0
                nocase_count = 0
                if ap == 1:
                    for i in range(0, num_classes):
                        a = s[:, :, i, :]
                        if len(a[a > -1]) == 0:
                            res = -1
                            nocase_count += 1
                        else:
                            res = np.mean(s[:, :, i, :])
                        print('category : {0} : {1}'.format(i, res))
                        if not res == -1:
                            avg_ap += res
                    print('(all categories) mAP : {}'.format(avg_ap / (num_classes - nocase_count)))
                else:
                    for i in range(0, num_classes):
                        a = s[:, i, :]
                        if len(a[a > -1]) == 0:
                            res = -1
                            nocase_count += 1
                        else:
                            res = np.mean(s[:, i, :])
                        print('category : {0} : {1}'.format(i, res))
                        if not res == -1:
                            avg_ap += res
                    print('(all categories) mAR : {}'.format(avg_ap / (num_classes - nocase_count)))
```

inspired by https://stackoverflow.com/questions/56247323/coco-api-evaluation-for-subset-of-classes

