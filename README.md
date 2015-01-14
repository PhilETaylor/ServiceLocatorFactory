# ServiceLocatorFactory

This is a long term fork of the fezfez/ServiceLocatorFactory as that is no longer maintained...

Allow you to get ServiceManager from everywhere in your application by calling this static factory. Yes its probably very bad practise to do it this way and not use complete DI, however sometimes you just gotta do what you gotta do.

Can be installed with composer - see https://packagist.org/packages/philetaylor/service-locator-factory

    <?php

    namespace Corp\News;

    use Corp\News\NewsDAO;
    use Zend\ServiceManager\ServiceManager;
    use Corp\ServiceLocator\ServiceLocator;

    class NewsDAOFactory
    {
        private function __construct()
        {
            
        }
    
        /**
         * @return \Corp\News\NewsDAO
         */
        public static function getInstance()
        {
            $sm = ServiceLocatorFactory::getInstance();
            $em = $sm->get('doctrine.entitymanager.orm_default');
    
            return new NewsDAO($em);
        }
    }
