# cocoevalbyclass

Print AP and AR by class when perform coco evaluation

to use this file, pycocotools/cocoeval.py should be modified as follow: 

in line 458 of cocoeval.py,

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

typical address of pycocotools/cocoeval.py :
/usr/local/anaconda3/envs/tensorflow/lib/python3.6/site-packages/pycocotools/cocoeval.py
/home/username/projects/RetinaNet_Tensorflow-master-lite/data/lib_coco/PythonAPI/pycocotools/cocoeval.py

inspired by https://stackoverflow.com/questions/56247323/coco-api-evaluation-for-subset-of-classes

