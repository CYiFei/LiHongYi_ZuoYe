# 对比李宏毅助教的代码，要跑起来需要做一些修改
###1
修改切割代码路径为label = int(fname.split("\\")[-1].split("_")[0])，解决找不到文件的错误
###2
batch_size设置为大于1，
避免下面代码循环时
for data, _ in test_loader:
    test_pred = model_best(data.to(device))
    test_label = np.argmax(test_pred.cpu().data.numpy(), axis=1)
    prediction += test_label.squeeze().tolist()
出现TypeError: 'int' object is not iterable错误
