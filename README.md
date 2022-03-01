# assignment3

Step 1: Create Project directory 
Step 2: Open terminal in 'project main directory'
Step 3: Run following commands
    npm init <!-- initialize the package.json file  -->
    npm install gulp -D <!-- install gulp package and dependencie -->
    npm install sass gulp-sass -D <!-- install sass and gulp-sass package and dependencie -->
    npm install sass gulp-sass -D <!-- install sass and gulp-sass package and dependencie -->
    npm install gulp-uglifycss -D <!-- install css minified package and dependencie -->

Step 4: create a file rename gulpfile.js in project main directory
Step 5: Write blow code into gulpfile.js
    <!-- code start -->
    var gulp = require('gulp');
    const sass = require('gulp-sass')(require('sass'));
    var uglifycss = require('gulp-uglifycss');
    <!-- compile scss to css -->
    gulp.task('scss', function(){
        return gulp.src('./scss/*.scss')
          .pipe(sass().on('error', sass.logError))
          .pipe(gulp.dest('./css'));
    });
    <!-- css minified -->
    gulp.task('css', function(){
        gulp.src('./css/*.css')
        .pipe(uglifycss({
            "uglyComments": true
        }))
        .pipe(gulp.dest('./dist'));
    });
    gulp.task('run', gulp.series('scss', 'css'));
    <!-- watch gulp task -->
    gulp.task('watch', function(){
        gulp.watch('./scss/*.scss', ['scss']);
        gulp.watch('./css/*.css', ['css']);
    });
    <!-- default gulp task -->
    gulp.task('default', gulp.series('run', 'watch'));
    <!-- code end -->
    
Step 6: Scss files Structures
    <!-- directory -->
    scss
        <!-- files -->
        style.scss
        _main.scss
        _color.scss
        _global.scss

Step 7: Run default command to compile scss into css
    Default command: gulp