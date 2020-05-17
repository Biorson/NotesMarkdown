观察者模式：将主题事件主动的通知给订阅过该主题事件的观察者们，主动的推数据给观察者或者提供方法供观察者们拉数据。

一个原则：交互对象间的松耦合。—通过互相的组合，观察者模式实现了对象间的松耦合

主题类

class Subject

{

public:

​    Subject();

​    ~Subject()

​    {

​        m_observer.clear();

​    }

​    void registerObserver(Observer * observer)

​    {	//判断vector不存在该observer

​        m_observer.push_back(observer);

​    }

​    void removeObserver(Observer * observer)

​    {

​        for(int i = 0;i<m_observer.size();i++)

​        {

​            if(m_observer.at(i) == observer)

​            {	

​                m_observer.erase(m_observer.begin()+i);

​                return ;

​            }

​        }

​    }

​    void notifyObserver()

​    {	

​        for(int i = 0;i < m_observer.size();i++)

​            m_observer.at(i)->update();

​    }

private:

​    vector<Observer  *> m_observer;

};

观察者类

class Observer

{

public:

​    Observer(Subject * subject)

​    {	

​        m_subject = subject;

​        m_subject->registerObserver(this);

​    }

​    ~Observer()

​    {

​        delete m_subject;

​    }

​    void update()

​    {

​        //取数据 ///

​    }

private:

​    Subject * m_subject;

};

Subject * s = new Subject();

Observer * o = new Observer(s);

Subject中可以再加入Flag,以控制是否向观察者对象下发通知。



一个原则：对扩展开放，对修改关闭。

装饰者模式通过装饰者给组件对象进行动态的附加责任，实现了组件对象对修改的关闭，对扩展的开放。提供了有别于继承的另一种扩展功能的选择。

装饰者和组件对象需要有一个共同的基类，以满足类型要求。

class Component  //装饰者和组件共同的基类

{

public:

​    Componet()；

​    ~Componet()；

​    String getdescription();

​    double cost();

protected:

​    String m_description;

​    double m_price;

}

//组件1 

class ConcreteComponet1:public Component  

{

public:

​    ConcreteComponet1()

​    {

​        m_price = 90.9;

​           m_description = "组件1 "；

​    }

​    String getdescription()

​    {

​        return m_description;

​    }

​    double cost()

​    {

​        return m_price;

​    }

}

//装饰者共同的基类

class Decorator:public Component

{

public:

​    Decorator();

​    ~Decorator();

​    virtual String getdescription()  = 0 ;

​    virtual double cost() = 0;

protected:

​    String m_description;

​    double m_price;

​      Component  * m_ Component ;

}

class ConcreteDecorator1:public Decorator

{

public:

​    ConcreteDecorator1(Component  * component  )

​    {

​        m_component = component;  

​        m_price = 90.9;

​           m_description = "装饰者1 "；

​    }

​    String getdescription()

​    {

​        return m_description + ;

​    }

​    double cost()

​    {

​        return m_price;

​    }

}