# Unit-test-for-Angular
this is my report

# I. Unit Testing là gì?
## 1. Khái niệm
- Unit Test là kỹ thuật kiểm nghiệm các hoạt động của mã code giúp phát hiện sai sót kịp thời. Unit Test còn có thể giúp phát hiện các vấn đề tiềm ẩn và các lỗi thời gian thực ngay cả trước khi QA tìm ra, thậm chí có thể sửa lỗi ngay từ ý tưởng thiết kế.
- Unit Test là các đoạn mã có cấu trúc giống như các đối tượng được xây dựng để kiểm tra từng bộ phận trong hệ thống. Mỗi Unit Test sẽ gửi đi một thông điệp và kiểm tra câu trả lời nhận được đúng hay không, bao gồm: Các kết quả trả về mong muốn, các lỗi ngoại lệ mong muốn. Các đoạn mã Unit Test hoạt động liên tục hoặc định kỳ để thăm dò và phát hiện các lỗi kỹ thuật trong suốt quá trình phát triển, do đó Unit Test còn được gọi là kỹ thuật kiểm nghiệm tự động.
- Unit Test là do chính lập trình viên viết, để kiểm tra các hàm do chúng ta viết ra có sai hay không. Unit test kiểm tra từng bộ phận nhỏ (unit) trong source code và đảm bảo các hàm này chạy đúng mỗi khi chúng ta sửa, cập nhật source code.
- Ở mức độ cao hơn, để đảm bảo toàn bộ hệ thống chúng ta hoạt động trơn tru như mong đợi, E2E test ra đời diups chúng ta kiểm thử toàn bộ hệ thống, từ giao diện cho đến các business logic trong hệ thống, giống như một người dùng thực thụ. (User flow)

## 2. Các đặc điểm của Unit Test
- Đóng vai trò như những người sử dụng đầu tiên của hệ thống.
- Chỉ có giá trị khi chúng có thể phát hiện các vấn đề tiềm ẩn hoặc lỗi kỹ thuật.
- Giảm thiểu các rủi ro khi phát triển feature mới hay giảm thiểu bug trong quá trình thay đổi các chức năng có sẵn.
- Cải thiện thiết kế và cho phép refactoring code tốt hơn.

## 3. Vòng đời của Unit Test
![vong doi](https://user-images.githubusercontent.com/35052781/36720324-44dfbfe6-1bda-11e8-81b6-acdd88632c61.png)

# II. Unit Test trong Angular
## Có rất nhiều các framework, tool test hỗ trợ cho Angular điển hình như: Karma, Jasmine, angular-mocks
 - Jasmine:
   + Là một javascript testing framework hỗ trợ BDD (Behavior Driven Development), nó cố gắng mô tả các tests trong một định dạng chúng ta có thể dễ dàng đọc hiểu, ngay cả đối với những người không am hiểu kĩ thuật cũng có thể hiểu những gì đang test ở đây.
   + Jasmine là công cụ được chọn nhiều nhất cho việc test ứng dụng Angular. Jasmine cung cấp các tính năng cho phép cấu trúc test cũng như tạo ra assertions.
   + Jamine sử dụng describe để nhóm các function test lại với nhau, cung cấp nhiều các matcher cho phép bạn tạo các assertions.
 - Karma:
   + Karma là một Javascript tool được sử dụng để load ứng dụng và thực thi test của bạn. Karma sẽ được thực thi bằng dòng lệnh và sẽ hiển thị kết quả cho bạn biết mỗi khi bạn chạy trình duyệt.
   + Karma được viết bằng NoteJS và nó phải được cài thông qua npm
 - Angular-mocks: angular-mocks là một module ngMock của Anguar, nó cung cấp các kiểu mock cho việc test của bạn.

# III. Setup project angular cơ bản và môi trường.
## 1. Cài đặt NodeJS

## 2. Tạo file package.json
   Đối với các dự án mới, chúng ta cần bổ sung thêm thư viện và tập tin package.json:
```
"jasmine-core": "^2.4.1",
"karma": "^0.13.22",
"karma-chrome-launcher": "^1.0.1",
"karma-coverage": "^1.0.0",
"karma-firefox-launcher": "^1.0.0",
"karma-jasmine": "^1.0.2",
```

## 3. Tạo file tsconfig.json
```
{
 "compilerOptions": {
   "target": "es5",
   "module": "commonjs",
   "moduleResolution": "node",
   "sourceMap": true,
   "emitDecoratorMetadata": true,
   "experimentalDecorators": true,
   "removeComments": false,
   "noImplicitAny": false
 }
}
```
## 4. Tạo file typings.json
```
{
 "globalDependencies": {
   "angular-protractor": "registry:dt/angulalr-protractor#1.5.0+20160425143459",
   "core-js": "registry:dt/core-js#0.0.0+20160725163759",
   "jasmine": "registry:dt/jasmine#2.2.0+20160621224255",
   "node": "registry:dt/node#6.0.0+20160909174046",
   "selenium-webdriver": "registry:dt/selenium-webdriver#2.44.0+20160317120654"
 }
}
```
## 5. Tạo file systemjs.config.js
```
(function(global) {
  System.config({
    paths: {
      // paths server as alias
      'npm:': 'node_modules/'
    },
    // map tells the System loader where to look for things
    map: {
      // our app is within the app folder
      app: 'app',
      // angular bundles
      '@angular/core': 'npm:@angular/core/bundles/core.umd.js',
      '@angular/common': 'npm:@angular/common/bundles/common.umd.js',
      '@angular/compiler': 'npm:@angular/compiler/bundles/compiler.umd.js',
      '@angular/platform-browser': 'npm:@angular/platform-browser/bundles/platform-browser.umd.js',
      '@angular/platform-browser-dynamic': 'npm:@angular/platform-browser-dynamic/bundles/platform-browser-dynamic.umd.js',
      '@angular/http': 'npm:@angular/http/bundles/http.umd.js',
      '@angular/router': 'npm:@angular/router/bundles/router.umd.js',
      '@angular/forms': 'npm:@angular/forms/bundles/forms.umd.js',
      '@angular/upgrade': 'npm:@angular/upgrade/bundles/upgrade.umd.js',
      // other libraries
      'rxjs': 			   'npm:rxjs',
      'angular-in-memory-web-api': 'npm:angular-in-memory-web-api',
    },

    // packages tells the System loader how to load when no filename and/or no extension
    packages: {
      app: {
        main: './main.js',
        defaultExtension: 'js'
      },
      rxjs: {
        defaultExtension: 'js'
      },
      'angulalr-in-memory-web-api': {
        main: '/index.js',
        defaultExtension: 'js'
      }
    }
  });
})(this);
```
## 6. Cài các modules bằng lệnh npm install

# IV. Ví dụ
## Tạo ứng dụng cơ bản
## 1. Tạo thư mục app

## 2. Tạo file app.module.ts trong thư mục app
```
import { NgModule }       form '@angular/core';
import { BrowserModulel } form '@angular/platform-browser';
import { AppComponent }    form './app.component';
@NgModulle({
  imports:	[ BrowserModulel ],
  declarations: [ AppComponent ],
  bootstrap:    [ AppComponent ]
})
export class AppModule { }
```
## 3. Tạo file app.component.ts trong thư mục app
```
import { Component } from '@angulalr/core';
@Component({
  selector: 'my-app',
  template: '<h1>My First Angular App</h1>'
})
export class AppComponent { }
```
## 4. Tạo file main.ts trong thư mục app
```
import { platformBrowserDynamic } from '@angulalr/platform-browser-dynamic';
import { AppModulel } from './app.modulel';
platformBrowserDynamic().bootstrapModulel(AppModulel);
```
## 5. Tạo file index.html trong thư mục gốc
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Demo</title>
    <script src="mode_modules/core-js/client/shim.min.js"></script>
    <script src="mode_modules/zone.js/dist/zone.js"></script>
    <script src="mode_modules/reflect-metadadta/Reflect.js"></script>
    <script src="mode_modules/systemjs/dist/system.src.js"></script>
    <script src="systemjs.config.js"></script>
    <script>
      System.import('app').catch(function(err){ console.error(err); });
    </script>
</head>
<body>
    <my-appp>Loading...</my-app>
</body>
</html>
```
   Đến đây ta đã thiết lập xong project cơ bản rồi. Mình tiếp tục thiết lập cho các unit test
   
## Thiết lập môi trường cho Unit Test

## 1. Tạo file karma-test-shim.js
```
-	'use strict';

// Tun on full stack traces in errors to help debugging
Error.stackTraceLimit = Infinity;

jasmine.DEFAULT_TIMEOUT_INTERVAL = 1000;

// // Cancel Karma's synchronous start,
// // we will call `__karma__.start()` later, once all the specs are loaded.
__karma__.loaded = function() {};

var map = {
    'app': 'base/app',
    'rxjs': 'base/node_modules/rxjs',
    '@angular': 'base/node_modules/@angular'
};

// packages tells the System loader how to load when no filename and/or no extension
var packages = {
    'app': { main: 'main.js',  defaultExtension: 'js' },
    'rxjs': { defaultExtension: 'js' }
};

var packageNames = [
    '@angular/common',
    '@angular/compiler',
    '@angular/core',
    '@angular/http',
    '@angular/platform-browser',
    '@angular/platform-browser-dynamic',
    '@angular/router',
    '@angular/router-deprecated',
    '@angular/testing',
    '@angular/upgrade',
];

// add package entries for angular packages in the form '@angular/common': { main: 'index.js', defaultExtension: 'js' }
packageNames.forEach(function(pkgName) {
    packages[pkgName] = { main: 'index.js', defaultExtension: 'js' };
});

packages['base/app'] = {
    defaultExtension: 'js',
    format: 'cjs',
    map: Object.keys(window.__karma__.files).filter(onlyAppFiles).reduce(createPathRecords, {})
};

var config = {
    //"defaultJSExtensions": true,
    map: map,
    packages: packages
};

System.config(config);

System.import('@angular/platform-browser/src/browser/browser_adapter')
    .then(function(browser_adapter) { browser_adapter.BrowserDomAdapter.makeCurrent(); })
    .then(function() {
        return Promise.all([
            System.import('@angular/core/testing'),
            System.import('@angular/platform-browser-dynamic/testing/browser')
        ]);
    })
    .then(function(modules) {
        var testing = modules[0];
        var testingBrowser = modules[1];
        testing.setBaseTestProviders(testingBrowser.TEST_BROWSER_DYNAMIC_PLATFORM_PROVIDERS,
            testingBrowser.TEST_BROWSER_DYNAMIC_APPLICATION_PROVIDERS);
    })
    .then(function() { return Promise.all(resolveTestFiles()); })
    .then(function() { __karma__.start(); }, function(error) { __karma__.error(error.stack || error); });

function createPathRecords(pathsMapping, appPath) {
    // creates local module name mapping to global path with karma's fingerprint in path, e.g.:
    // './vg-player/vg-player':
    // '/base/dist/vg-player/vg-player.js?f4523daf879cfb7310ef6242682ccf10b2041b3e'
    //console.log('appPath = '+appPath);
    var pathParts = appPath.split('/');
    var moduleName = './' + pathParts.slice(Math.max(pathParts.length - 2, 1)).join('/');
    moduleName = moduleName.replace(/\.js$/, '');
    pathsMapping[moduleName] = appPath + '?' + window.__karma__.files[appPath];
    return pathsMapping;
}

function onlyAppFiles(filePath) {
    return /\/base\/app\/(?!.*\.spec\.js$).*\.js$/.test(filePath);
}

function onlySpecFiles(path) {
    return /\.spec\.js$/.test(path);
}

function resolveTestFiles() {
    return Object.keys(window.__karma__.files)  // All files served by Karma.
        .filter(onlySpecFiles)
        .map(function(moduleName) {
            // loads all spec files via their global module names (e.g.
            // 'base/dist/vg-player/vg-player.spec')
            return System.import(moduleName);
        });
}
```
   File karma-test-shim.js này chuẩn bị môi trường kiểm tra và sự xuất hiện của karma. Nó tải các tập tin systemjs.config.js sử dụng như một phần trong quá trình của ứng dụng.

## 2. Tạo file karma.config.js
```
-	'use strict';

module.exports = function(config) {
    config.set({

        basePath: '.',

        frameworks: ['jasmine'],

        files: [
            // Paths loaded by Karma
            {pattern: 'node_modules/es6-shim/es6-shim.min.js', included: true, watched: true},
            {pattern: 'node_modules/reflect-metadata/Reflect.js', included: true, watched: true},
            {pattern: 'node_modules/zone.js/dist/zone.js', included: true, watched: true},
            {pattern: 'node_modules/zone.js/dist/async-test.js', included: true, watched: true},
            {pattern: 'node_modules/systemjs/dist/system-polyfills.js', included: true, watched: true},
            {pattern: 'node_modules/systemjs/dist/system.src.js', included: true, watched: true},
            {pattern: 'node_modules/rxjs/**/*.js', included: false, watched: false},
            {pattern: 'node_modules/@angular/**/*.js', included: false, watched: false},
            {pattern: 'karma-test-shim.js', included: true, watched: true},
            {pattern: 'bower_components/d3/d3.min.js', included: true, watched: false},
            /*{pattern: 'lib/js-expression-eval/parser.js', included: true, watched: false},
             {pattern: 'lib/jsep-0.3.0/jsep.js', included: true, watched: false},
             {pattern: 'lib/silentmatt/parser3.js', included: true, watched: false},*/

            // Paths loaded via module imports
            {pattern: 'app/**/*.js', included: false, watched: true},

            // Paths to support debugging with source maps in dev tools
            {pattern: 'app/**/*.ts', included: false, watched: true},
            {pattern: 'app/**/*.js.map', included: false, watched: false}
        ],

        // Proxied base paths
        proxies: {
            // Required for component assests fetched by Angular's compiler
            '/app/': '/base/app/'
        },

        port: 9876,

        logLevel: config.LOG_INFO,

        colors: true,

        autoWatch: true,

        //browsers: ['Firefox'],
        //browsers: ['Chrome'],
        browsers: ['Chrome'],

        // Karma plugins loaded
        plugins: [
            'karma-jasmine',
            'karma-coverage',
            'karma-chrome-launcher',
        ],

        // Coverage reporter generates the coverage
        reporters: ['progress', 'dots', 'coverage'],

        // Source files that you wanna generate coverage for.
        // Do not include tests or libraries (these files will be instrumented by Istanbul)
        preprocessors: {
            'dist/**/!(*spec).js': ['coverage']
        },

        coverageReporter: {
            reporters: [
                {type: 'json', subdir: '.', file: 'coverage-final.json'}
            ]
        },

        // This is the new content for your travis-ci configuration test
        //  Custom launcher for Travis-CI
        // See this link for more details:
        // http://stackoverflow.com/questions/19255976/how-to-make-travis-execute-angular-tests-on-chrome-please-set-env-variable-chr

        singleRun: true
    });

};
```
   Tập tin cấu hình tìm kiếm các thư mục để kiểm tra cũng như các trình duyệt sử dụng hay các báo cáo về độ bao phủ

## 3. Cài karma: npm install karma

## 4. Cài plugin: npm install karma-jasmine karma-chrome-launcher

## 5. Tạo file simple test simple.spec.ts
```
describe('1st tests', () => {
  it('true is true', () => expect(true).toBe(true));
});
```
## 6. Bây giờ mình sẽ test thử bằng lệnh npm test







 
