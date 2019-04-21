# -
设计模式

facade
//https://www.cnblogs.com/lwbqqyumidi/p/3754251.html

//各个接口
xxxxxxxx
class HealthOffice implements Executive{
    @Override
    public void approve() {
        System.out.println("卫生局通过审批");
    } 
}
//调用接口
public class FacadeTest {
    public static void main(String[] args) {
        System.out.println("开始办理行政手续...");

        HealthOffice ho = new HealthOffice();
        RevenueOffice ro = new RevenueOffice();
        SaicOffice so = new SaicOffice();

        ho.approve();
        ro.approve();
        so.approve();
        System.out.println("行政手续终于办完了");
    }
}

facade 模式
//低耦合，减少对子系统的交互，方便扩展管理
class ApproveFacade {
    public ApproveFacade() {
    }
    public void wholeApprove() {
        new HealthOffice().approve();
        new RevenueOffice().approve();
        new SaicOffice().approve();
    }
}

public class FacadeTest {
    public static void main(String[] args) {
        System.out.println("开始办理行政手续...");
        ApproveFacade af = new ApproveFacade();
        af.wholeApprove();   
        System.out.println("行政手续终于办完了");
    }
}

Factory

工厂模式适用场景
    1、当一个类不知道它所必须创建的对象的类的时候
    2、当一个类希望由它的子类来指定它所创建的对象的时候
    3、当类将创建对象的职责委托给多个帮助子类的某一个，并且你希望将哪一个帮助子类是代理者这一信息局部化的时候
     如果您想要更改所创建的对象类型，只需更改该工厂即可。使用该工厂的所有代码会自动更改。    


    public static function getInstance($className, $options = null){
        if (!isset(self::$Factory[$className]) || !self::$Factory[$className]) {
            self::$Factory[$className] = new $className($options);
        }
        return self::$Factory[$className];
    }
