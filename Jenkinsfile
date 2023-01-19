@Library('global-jenkins-library@feature/add-credentials-secrets') _
import com.iexec.jenkins.deployment.Service
import com.iexec.jenkins.deployment.ServiceDeploymentConfig
import com.iexec.jenkins.deployment.ServiceSecret

eth-netstat-serv = new Service(
        rootDir: 'net-stat',
        devHost: 'azub004govvx.viviani-services.az2.internal',
        prodHost: 'governance.bellecour-services.az2.internal',
        devSecrets: [
            new ServiceSecret('ws_secret', 'ws_secret'),
        ],
        prodSecrets: [
            new ServiceSecret('ws_secret', 'ws_secret'),

        ]
    )

stage('Select service') {

    targetEnv = 'dev'
    targetService = eth-netstat-serv
    println "targetEnv: $targetEnv"
    println "targetService: $targetService"
}


deploySimpleDocker_v2(
    new ServiceDeploymentConfig(
        targetService: targetService ,
        targetEnv: targetEnv,
        jenkinsNode: 'docker',
        updateSeed: false
    )
)


