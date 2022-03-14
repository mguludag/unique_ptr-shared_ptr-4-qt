# unique_ptr-shared_ptr-4-qt
std::unique_ptr and std::shared_ptr aliases for QObject based types also built-in custom deleters for it. For example if object is QThread or any subclass of QThread the deleter quits the thread before delete the pointer.

## Usage
*mainwindow.hpp*  
```C++
#include "qmemory.hpp"
#include <QDialog>

class MainWindow
{
public:
  ...

private:
  stdx::qt::unique_ptr<QDialog> d;
};
```
*mainwindow.cpp*  

```C++
#include "mainwindow.hpp"
...

MainWindow::MainWindow()
{
  d = stdx::qt::make_unique<QDialog>(...);
  ...
}
...
```

