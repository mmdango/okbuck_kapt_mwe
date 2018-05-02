# okbuck_kapt_mwe

This is a MWE of a failing Okbuck (v0.37.3) build with the Butterknife annotation processor.

Notes: Happens with both Butterknife versions 8.8.1 and 9.0.0-SNAPSHOT

To reproduce:
run: `./buckw build //app:bin_release`

and observe the following error message/stacktrace:

```Build failed: Command failed with exit code 2.
stderr: logging: using Kotlin home directory /Users/michael_dang/.sdkman/candidates/kotlin/1.2.40
logging: configuring the compilation environment
exception: java.util.ServiceConfigurationError: javax.annotation.processing.Processor: Provider butterknife.compiler.ButterKnifeProcessor could not be instantiated
	at java.util.ServiceLoader.fail(ServiceLoader.java:232)
	at java.util.ServiceLoader.access$100(ServiceLoader.java:185)
	at java.util.ServiceLoader$LazyIterator.nextService(ServiceLoader.java:384)
	at java.util.ServiceLoader$LazyIterator.access$700(ServiceLoader.java:323)
	at java.util.ServiceLoader$LazyIterator$2.run(ServiceLoader.java:407)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.ServiceLoader$LazyIterator.next(ServiceLoader.java:409)
	at java.util.ServiceLoader$1.next(ServiceLoader.java:480)
	at kotlin.collections.CollectionsKt___CollectionsKt.toCollection(_Collections.kt:1074)
	at kotlin.collections.CollectionsKt___CollectionsKt.toMutableList(_Collections.kt:1107)
	at kotlin.collections.CollectionsKt___CollectionsKt.toList(_Collections.kt:1098)
	at org.jetbrains.kotlin.kapt3.ClasspathBasedKapt3Extension.loadProcessors(Kapt3Extension.kt:114)
	at org.jetbrains.kotlin.kapt3.AbstractKapt3Extension.analysisCompleted(Kapt3Extension.kt:206)
	at org.jetbrains.kotlin.kapt3.ClasspathBasedKapt3Extension.analysisCompleted(Kapt3Extension.kt:95)
	at org.jetbrains.kotlin.cli.jvm.compiler.TopDownAnalyzerFacadeForJVM$analyzeFilesWithJavaIntegration$2.invoke(TopDownAnalyzerFacadeForJVM.kt:97)
	at org.jetbrains.kotlin.cli.jvm.compiler.TopDownAnalyzerFacadeForJVM.analyzeFilesWithJavaIntegration(TopDownAnalyzerFacadeForJVM.kt:107)
	at org.jetbrains.kotlin.cli.jvm.compiler.TopDownAnalyzerFacadeForJVM.analyzeFilesWithJavaIntegration$default(TopDownAnalyzerFacadeForJVM.kt:84)
	at org.jetbrains.kotlin.cli.jvm.compiler.KotlinToJVMBytecodeCompiler$analyze$1.invoke(KotlinToJVMBytecodeCompiler.kt:374)
	at org.jetbrains.kotlin.cli.jvm.compiler.KotlinToJVMBytecodeCompiler$analyze$1.invoke(KotlinToJVMBytecodeCompiler.kt:64)
	at org.jetbrains.kotlin.cli.common.messages.AnalyzerWithCompilerReport.analyzeAndReport(AnalyzerWithCompilerReport.kt:101)
	at org.jetbrains.kotlin.cli.jvm.compiler.KotlinToJVMBytecodeCompiler.analyze(KotlinToJVMBytecodeCompiler.kt:365)
	at org.jetbrains.kotlin.cli.jvm.compiler.KotlinToJVMBytecodeCompiler.analyzeAndGenerate(KotlinToJVMBytecodeCompiler.kt:350)
	at org.jetbrains.kotlin.cli.jvm.compiler.KotlinToJVMBytecodeCompiler.compileBunchOfSources(KotlinToJVMBytecodeCompiler.kt:245)
	at org.jetbrains.kotlin.cli.jvm.K2JVMCompiler.doExecute(K2JVMCompiler.kt:207)
	at org.jetbrains.kotlin.cli.jvm.K2JVMCompiler.doExecute(K2JVMCompiler.kt:63)
	at org.jetbrains.kotlin.cli.common.CLICompiler.execImpl(CLICompiler.java:107)
	at org.jetbrains.kotlin.cli.common.CLICompiler.execImpl(CLICompiler.java:51)
	at org.jetbrains.kotlin.cli.common.CLITool.exec(CLITool.kt:96)
	at org.jetbrains.kotlin.cli.common.CLITool.exec(CLITool.kt:72)
	at org.jetbrains.kotlin.cli.common.CLITool.exec(CLITool.kt:38)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at com.facebook.buck.jvm.kotlin.JarBackedReflectedKotlinc.buildWithClasspath(JarBackedReflectedKotlinc.java:172)
	at com.facebook.buck.jvm.kotlin.KotlincStep.execute(KotlincStep.java:93)
	at com.facebook.buck.step.DefaultStepRunner.runStepForBuildTarget(DefaultStepRunner.java:45)
	at com.facebook.buck.rules.CachingBuildRuleBuilder$BuildRuleSteps.executeCommands(CachingBuildRuleBuilder.java:1325)
	at com.facebook.buck.rules.CachingBuildRuleBuilder$BuildRuleSteps.executeCommandsNowThatDepsAreBuilt(CachingBuildRuleBuilder.java:1293)
	at com.facebook.buck.rules.CachingBuildRuleBuilder$BuildRuleSteps.runWithExecutor(CachingBuildRuleBuilder.java:1252)
	at com.facebook.buck.rules.CachingBuildRuleBuilder$BuildRuleSteps.run(CachingBuildRuleBuilder.java:1241)
	at com.facebook.buck.rules.CachingBuildRuleBuilder$2.runWithDefaultExecutor(CachingBuildRuleBuilder.java:755)
	at com.facebook.buck.util.concurrent.WeightedListeningExecutorService.lambda$submit$2(WeightedListeningExecutorService.java:104)
	at com.facebook.buck.util.concurrent.WeightedListeningExecutorService.lambda$submitWithSemaphore$0(WeightedListeningExecutorService.java:78)
	at com.google.common.util.concurrent.AbstractTransformFuture$AsyncTransformFuture.doTransform(AbstractTransformFuture.java:206)
	at com.google.common.util.concurrent.AbstractTransformFuture$AsyncTransformFuture.doTransform(AbstractTransformFuture.j  1 # okbuck_kapt_mwe
ava:195)
	at com.google.common.util.concurrent.AbstractTransformFuture.run(AbstractTransformFuture.java:115)
	at com.google.common.util.concurrent.MoreExecutors$5$1.run(MoreExecutors.java:999)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1142)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:617)
	at java.lang.Thread.run(Thread.java:745)
Caused by: java.lang.NoClassDefFoundError: com/sun/tools/javac/tree/JCTree$Visitor
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:2671)
	at java.lang.Class.getConstructor0(Class.java:3075)
	at java.lang.Class.newInstance(Class.java:412)
	at java.util.ServiceLoader$LazyIterator.nextService(ServiceLoader.java:380)
	... 48 more
Caused by: java.lang.ClassNotFoundException: com.sun.tools.javac.tree.JCTree$Visitor
	at java.net.URLClassLoader.findClass(URLClassLoader.java:381)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:424)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:357)
	... 53 more


    When running <kotlinc>.
    When building rule //app:src_release.```
